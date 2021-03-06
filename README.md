 yii2-password
==============

This extension provides a couple of great password management utilities for Yii Framework 2.0. The extension allows password strength validation through your model. In addition, it provides an advanced password input widget, that allows you to display/hide text and show the password strength.

### StrengthValidator
[```VIEW DEMO```](http://demos.krajee.com/password-details/strength-validator)  
This is a password strength validator for your model attributes. The strength validator allows you to configure the following parameters for validating passwords or strings.

1. Whether password contains an username
2. Whether password contains an email string
3. Minimum number of characters
4. Maximum number of characters
5. Minimum number of lower space characters
6. Minimum number of upper space characters
7. Minimum number of numeric / digit characters
8. Minimum number of special characters

Other features:

1. Includes 5 presets (simple, normal, fair, medium, and strong). Instead of setting each parameter above, you can call a preset which will auto-set each of the parameters above. 
2. It includes both server and client validation. 
3. This can work with the PasswordInput widget (described next) as per your needs. The strength validation routines for both are a bit different. The PasswordInput widget focuses on displaying the strength only, and does not restrict the user input in any way.

> NOTE: The StrengthValidator does not validate if the password field is required. You need to use Yii's ```required``` rule for this.

### PasswordInput
[```VIEW DEMO```](http://demos.krajee.com/password-details/password-input)  
This is an advanced password input widget with configurable options and a dynamic strength meter based on the [Strength Meter JQuery Plugin](http://plugins.krajee.com/strength-meter) by Krajee. The widget provides various features as mentioned below:

1. Allows you to show/ hide a password text (using bootstrap styled input addons). You can configure this option to be shown or not.
2. Allows you to display an advanced password strength meter to calculate and show your password strength as you type. 
3. Allows you to control and position/style your meter based on templates.
4. A password strength meter consists of the meter bar, the score, and the verdict.
5. Uses Bootstrap 3.0 styling wherever possible with inbuilt Yii 2.0 ActiveField functionality.
6. Works independent and complements the StrengthValidator.

### Demo
You can see a [demonstration here](http://demos.krajee.com/password) on usage of these functions with documentation and examples.

## Installation

The preferred way to install this extension is through [composer](http://getcomposer.org/download/).

Either run

```
$ php composer.phar require kartik-v/yii2-password "dev-master"
```

or add

```
"kartik-v/yii2-password": "dev-master"
```

to the ```require``` section of your `composer.json` file.

## Usage

### StrengthValidator
```php
// add this in your model
use kartik\password\StrengthValidator;

// use the validator in your model rules
public function rules() {
    return [
       	[['username', 'password'], 'required'],
       	[['password'], StrengthValidator::className(), 'preset'=>'normal', 'userAttribute'=>'username']
    ];
}
```

### PasswordInput
```php
// add this in your view
use kartik\password\PasswordInput;
use kartik\widgets\ActiveForm; // optional

$form = ActiveForm::begin(['id' => 'login-form']);
echo $form->field($model,'username');
echo $form->field($model, 'password')->widget(PasswordInput::classname(), [
	'showMeter' => true,
	'toggleMask' => false
]);
```

## License

**yii2-password** is released under the BSD 3-Clause License. See the bundled `LICENSE.md` for details.
