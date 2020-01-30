# Mobiforte SMS

This package provides a convenient way to send SMS from your Laravel application with mobiforte.com as a service provider.

## Installation

Download and install Composer (from ```http://www.getcomposer.org/download```) if you do not have it already installed on your machine.

#### Method 1:
Require this package:

```bash
composer require nanadjei2/mobiforte
```

#### Method 2:
Require this package:

```bash
{
    "require": {
       "nanadjei2/mobiforte": "0.1.*"
    }
}
```
and run this command.
```bash
composer update
```
After updating Composer, add the ServiceProvider to the providers array in config/app.php

### Laravel <= 5.4
If you're using Laravel 5.5 and above, you can skip this step.
```bash
Nanadjei2\Mobiforte\Mobiforte\MobiforteServiceProvider::class,
```
And the facade of the package to this package to the $aliase array.

```bash
'MobiforteSms' => Nanadjei2\Mobiforte\Facades\MobiforteSms::class
```

### Configuration
Before you can start sending SMS you will need to set your api keys and default sender ID in your ```.env``` file. You can find your api key and api secret here ```https://web.mobiforte.com/developer```

```
# In your root directory .env
# Note: Sender ID by default uses your app name (env('APP_NAME')). Sender Id must not exceed 11 characters.
MOBIFORTE_SMS_SENDER_ID=LaravelApp

MOBIFORTE_SMS_CLIENT_ID=YourClientId

MOBIFORTE_SMS_CLIENT_SECRET=YourClientSecrete
```

## Usage
Below is a basic usage guide for sending SMS and checking SMS balance of your Mobiforte account.

```bash
# Basically sending sms uses api key set in .env file.
 MobiforteSms::send('02XXXXXXXX', "Hello from the other side.");

# Want to use a different api key?
 MobiforteSms::withFreshApiKeys("fresh_client_id", "fresh_client_secret")
   ->send("02XXXXXXXX", "Say hello from the other side.");
```


## Contributing
Thank you for considering contributing to the package! To contribute, fork this repository, write some code and then submit a pull request to the develop branch 🤝

## License
[MIT](https://choosealicense.com/licenses/mit/)
