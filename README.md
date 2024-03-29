# Hyurs
Hyurs is a tool that will download data from your Google Calendar, let you create mappings between (calendar, event-name) pairs and hierarchical tags, and then generate reports and graphs of the hours taken up by various events.

For example, you might have an event in the calendar "Studying" called "revise computation theory". In a simple tagging system, maybe you'd get to tag it with "computation theory", but Hyurs is more fine-grained: you can give it a "hierarchical tag" like "computer science:computation theory:revision", that the calendar/event combination "Studying/revise computation theory" maps to.

Once the downloaded data and event mapping exists, you can continue syncing by (currently) simply running the setup script again; you won't have to create the mapping from scratch every time, but only for any (calendar, event name) pairs in the newly-downloaded calendar data that aren't yet mapped to anything.

The main purpose of Hyurs is that once you've done this, you can generate for any time period a report / pie chart / flame chart showing how you've spent time (in hours) across some set of your activities. The report will have a tree structure like this:

* computer science: 74
  * computation theory: 29
    * lectures: 9.5
    * supervision work: 14
    * revision: 3.5
  * ...
* ...

An example pie chart looks like this:

<img width="1440" alt="Example pie chart" src="https://user-images.githubusercontent.com/55555739/112853682-c7c52b00-90b5-11eb-9d4a-96dbb458af33.png">

Flame chart:

<img width="439" alt="image" src="https://user-images.githubusercontent.com/55555739/137621282-41e7897a-1e26-4029-ac63-99ff8506301b.png">


The graphs are very customisable: you can filter in or out based on a set of tags, choose what intervals to graph and how many, and so on.

## Dependencies

* The Google libraries listed [here](https://developers.google.com/calendar/quickstart/python), specifically: `google-api-python-client google-auth-httplib2 google-auth-oauthlib`.
* Currently, if you want direct Goolge Calendar sync, you also need to do some annoying setup things as specified on the [Google Calendar Python integration guide](https://developers.google.com/calendar/api/quickstart/python) so that your Google Calendar knows to trust Hyurs, including either contacting me so that I add you to the test users list for the Hyurs API, or creating your own Google Cloud API (simple but takes a while).
  * ALTERNATIVE: [Anthony Ozerov](https://github.com/anthonyozerov) made a pull request enabling sync from the standard iCalendar format (.ics).
* [Hy](https://docs.hylang.org/en/stable/) v0.20 or later.
* Python 3

## Use

Run `setup.py` (check file for arguments) to sync from Google Calendar (or .ics file) to Hyurs.

## Functional goal

The functional goal is to make it easy to track and visualise how much time you're spending on anything of your choice (studying, exercise, writing productivity software, etc.) at a fine-grained level, and integrate with an existing more-or-less polished tool (Google Calendar).

## Technical goal

Python is somewhat unfriendly to functional programming. However, it is also a powerful high-level language with libraries for everything. Thankfully, some people went and wrote [a Lisp called Hy](https://docs.hylang.org/en/stable/) that compiles to Python ASTs and therefore gives you access to all Python libraries. This project is partly a test of how feasible Hy is as a practical development language.

## Contributions, feature requests, and actually using Hyurs

I welcome any sensible pull requests.

Also, if you intend to start using this for yourself, do send a message and I will make a more detailed setup/use tutorial and in general make Hyurs more pleasant to use.
