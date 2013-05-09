Angular E2E Window Dialog Commands
==================================
Comprises four commands to interact with window.alert, window.confirm and window.prompt

Commands
--------
* `alertOK()` sets `window.alert` to return `true` when it is called in your application
* `confirmOK()` sets `window.confirm` to return true when it is called in your application
* `confirmCancel()` sets `window.confirm` to return false when it is called in your application
* `setPromptValue(value)` sets `window.prompt` to return `value` when it is called in your application

Installation
------------
Save `window-dialog-commands.js` file into your project (e.g. `test/e2e/`) and load it in the `test/e2e/runner.html` file

    <script src="../lib/angular/angular-scenario.js" ng-autotest></script>
    <script src="window-dialog-commands.js"></script>
    <script src="scenarios.js"></script>

Usage
-----
Execute the relevant command in the `it` block where your application is using a dialog box.

### alertOK
Given that your application is greeting the user with their name just after they log in you can use the `alertOK` as:

    it('should log in with a valid name', function() {
		alertOK();
        element(':submit').click();
        expect... // expect user to be signed in
    });

### confirmOK and confirmCancel
Given that your application is asking for user's confirmation when they want to logout you can then use `confirmOK` and `confirmCancel` in your tests as:

    it('should log out upon confirmation', function() {
        confirmOK();
        element('#logout').click();
        expect... // expect user to be logged out
    });

    it('shouldn\'t log out upon cancel', function() {
        confirmCancel();
        element('#logout').click();
        expect... // expect user to be still signed in
    });

### setPromptValue
Given that your application is asking the user to enter their name in a prompt you can then use `setPromptValue` in your tests as:

    it('should log in with a valid name', function() {
        setPromptValue('Ahmet');
        alertOK();
        expect... // expect user to be signed in
    });