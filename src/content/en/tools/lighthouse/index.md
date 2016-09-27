project_path: /web/_project.yaml
book_path: /web/tools/_book.yaml
description: Learn how to set up Lighthouse to audit your web apps.

{# wf_updated_on: 2016-09-27 #}
{# wf_published_on: 2016-09-27 #}

# Audit Web Apps With Lighthouse {: .page-title }

{% include "web/_shared/contributors/kaycebasques.html" %}

Lighthouse is an open-source, automated tool for improving the quality of
your web apps. You can run it as a Chrome Extension or from the command line.
You give Lighthouse a URL that you want to audit, it runs a barrage of tests
against the page, and then it generates a report on how well the page did.
From here you can use the failing tests as indicators on what you can do to
improve your app.

## Get started

There are two ways to run Lighthouse, as a Chrome Extension, or as a command
line tool. The Chrome Extension provides a more user-friendly interface for
reading reports. The command line tool enables you to integrate Lighthouse into
continuous integration systems.

### Chrome extensions

Download Google Chrome 52 or later.

Install the [Lighthouse Chrome Extension](https://chrome.google.com/webstore/detail/lighthouse/blipmdconlkpinefehnmjammfjpmpbjk).

Go to the page that you want to audit.

Click on the Lighthouse icon (![Lighthouse 
icon](images/lighthouse-icon-16.png)) that is on the Chrome toolbar.

![Lighthouse icon on Chrome Toolbar](images/icon-on-toolbar.png)

If you don't see the icon on your toolbar, it may be hidden in Chrome's
main menu.

![Lighthouse icon in Chrome's Menu](images/icon-in-menu.png)

After clicking on the icon, you should see a menu.

![Lighthouse menu](images/menu.png)

If you want to only run a subset of the audits, click the **Options** button
and disable the audits that you don't care about. Scroll down and press **OK**
to confirm your changes.

![Lighthouse options menu](images/options.png)

Click the **Generate report** button to run Lighthouse's tests against the
currently-open page.

When the audits are finished, Lighthouse opens up a new tab and displays a
report on the page's results.

![Lighthouse report](images/report.png)

### Command line tool

Install [Node](https://nodejs.org), version 5 or greater.

Install Lighthouse as a global Node module.

    npm install -g GoogleChrome/lighthouse

Run a Lighthouse audit against a page.

    lighthouse https://airhorner.com/

Pass the `--help` flag to see available input and output options.

    lighthouse --help
