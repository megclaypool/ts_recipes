# Behat Installation and Use

## Part 1: Initial setup

### Composer

The easiest way to install behat is with composer, so make sure it's installed.

`brew install composer`

### Behat

1. copy composer.json to the place where you want to run it.
This could be a project-specific directory or it could be common scripts location.
Either /projects/PROJECTNAME/behat or ~/behat will work.

2. Run `composer install` in the directory that contains composer.json.

3. Confirm that it is installed and let behat set up some default by running `behat --init`.

###  Selenium

1. Install the selenium server: `brew install selenium-server-standalone`

2. If you haven't already, add homebrew's integration with macOS's launchctl manager: `brew tap homebrew/services`

3. Use brew's services to launch the selenium server and restart it each time you restart your computer: `sudo brew services start selenium-server-standalone`

4. Confirm that it works by running in a new terminal session: `selenium-server`
There should be a message like "RemoteWebDriver instances should connect to: http://127.0.0.1:4444/wd/hub".
Confirm that that page loads. Quit by using CTRL-C in terminal.

## Part 2: Set up some tests and run them

1. Copy the contents of the features directory to your behat/features installation.
2. Copy behat.yml to your behat installation, and edit the base_url setting.
3. Start selenium. `selenium-server`
4. Run any of the following:
    - `behat features/contact_form.feature` (tests the one feature)
    - `behat features` (runs all tests in the features directory)
    - `behat` (runs all tests that behat can find.)

### Tips and further reading.
- `behat -di` to see all availble definitions (statements, assertions, etc).
- `behat --help` for all available commands and options.
- Use 'follow' for links, and 'press' for buttons.
- http://behat.org/
- http://docs.behat.org/quick_intro.html
- Writing features:
  - Tests are case sensitive.
  - http://docs.behat.org/cookbook/behat_and_mink.html#writing-your-first-web-feature
  - http://docs.behat.org/en/v3.0/guides/1.gherkin.html
- Adding custom definitions: http://docs.behat.org/cookbook/behat_and_mink.html#defining-our-own-featurecontext
  - `bin/behat --init` to set up some placeholder directories and scripts.
  - Then add `use Behat\MinkExtension\Context\MinkContext;` and extend MinkContext instead of BehatContext.
- http://mink.behat.org/ (Including http://mink.behat.org/#different-browsers-drivers)
- http://docs.behat.org/en/v3.0/ (Lots of good stuff in here.)
- For selenium and webdriver: https://github.com/facebook/php-webdriver/
- A good starting point: http://drupalwatchdog.com/volume-2/issue-2/behat-and-mink

### Examples
- http://cgit.drupalcode.org/panopoly_test/tree/tests
