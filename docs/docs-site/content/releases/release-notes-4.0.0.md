---
title: "4.0.0"
date: 2019-03-13T18:28:08-07:00
draft: false
weight: -4000
tags: ['skipIndexing']
---

### Hue v4.0.0, released June 9th 2017


Hue, http://gethue.com, is an open source Query Tool for analyzing data.

Its main features:

   * Editors for Hive, Impala, Spark, MapReduce and any SQL like MySQL, Oracle, PostGreSQL, SparkSQL, Solr SQL, Phoenix...
   * Dashboards to dynamically interact and visualize data with Solr or SQL
   * Scheduler of jobs and workflows
   * Browsers for Jobs, HDFS, S3 files, SQL Tables, Indexes, Git files, Sentry permissions, Sqoop...

Read the complete list of improvements on [Hue 4 and its new interface is out!
](http://gethue.com/hue-4-and-its-new-interface-is-out/).


Notable Changes
---------------

Interface

* The new layout simplifies the interface and is now single page and snappier. Various applications have been grouped into 4 applications:
   ** Editor
   ** Browsers
   ** Dashboard
   ** Scheduler
* A top search bar and left assist help quick search and browse any data.
* Each user can set its favorite application as default action / landing page.
* The older Hue 3 UI is still available and Hue 4 is 100% backward compatible.
* The switch to the new Hue 4 UI can be decided at global level or each user can independently flip back and forth with one of the UIs as default.
* All the URLs with the '/hue' prefix point to Hue 4, the one without still points to Hue 3.
* It is possible to just remove the prefix and land on the Hue 3 version of the page, e.g. /hue/editor (Hue 4) → /editor (Hue 3)


SQL Editor

* If multiple statements are present in the editor, the position of the cursor will determine what is the active statement that will be executed. In order to execute multiple statements (e.g. a series of CREATE tables) in sequence, they need to be manually highlighted or all selected via selected all shortcut (e.g. CTRL/CMD + A).

Pig Editor

* New editor, some advanced use of declare and macros are not supported in the new Editor autocomplete. Past scripts have been converted to the new editor, or can be found in the Hue 3 UI.

Job Designer

* Actions like MapReduce, Java, Spark, Sqoop1 now show up in the new editor. Past scripts have been converted to the new editor, or can be found in the Hue 3 UI.

Job Browser

* New browser now combining the previous Job Browser and Oozie Dashboard. The app is now single paged and more intuitive to use. A mini-job browser is now available to see jobs without leaving the page.

Oozie Editor

* Saved queries from the Editor (e.g. Hive query) can be directly dragged and dropped into an action without the need of copying the files on HDFS manually.

S3 Browser

* Support V2 regions if your credentials are configured for V2 region. If you are configured for a V4 endpoint, you can only access buckets for that region's endpoint.


Misc

* Create a partitioned table from a file
* Creating a table in the importer now refreshes Impala metadata automatically
* The SQL autocompleter handles more advanced corner cases
* Load balancers on a different host than Hue now work with SSL
* Pagination added to the SQL query history
* Batch operation like create tables now happens as background tasks
* 500 bug fixes


Compatibility
-------------

Runs on CentOS versions 5 to 6, Red Hat Enterprise Linux (RHEL 5, 6, 7), and Ubuntu 12.04, 14.04 and 16.04.

Tested with CDH5. Specifically:

- Hadoop 2.6.0
- Hive 1.1
- Oozie 4.1
- HBase 1.2
- Pig 0.12
- Impala 2.5
- Solr 4.10
- Sqoop2 1.99.5
- Spark 1.6

These minimum versions should work (not tested):

- Hadoop 0.20 / 1.2.0 / 2.0.0
- Hive 0.12.0
- Oozie 3.2
- HBase 0.92
- Pig 0.8
- Impala 1.0
- Solr 3.6
- Sqoop2 1.99.3
- Spark 1.4

Supported Browsers:

Hue works with the two most recent versions of the following browsers. Make sure cookies and JavaScript are turned on for the browser.

* Chrome
* Firefox LTS
* Safari (not supported on Windows)
* Internet Explorer

Hue might work with Chrome 23, Firefox 23, IE8, Safari 6, or older browser version, but you might not be able to use all of the features.


Runs with Python 2.6.5+

Note: CentOS 5 and RHEL 5 requires EPEL python 2.6 package.


List of 3215 Commits
--------------------
* 255feb3 HUE-6674 [doc] Add 4.0 release notes
* 2b7fce0 HUE-6665 [jb] Reset pagination when updating the filters
* 65cebf4 HUE-6662 [jb] Interface slas is unknown on SLA tab
* a549f79 HUE-6663 [jb] Oozie pagination is not showing the total number of jobs
* 9996b11 HUE-6664 [jb] Make configurable the number of jobs fetched without pagination
* c46dcde HUE-6661 [editor] Hide save button in external statement as not implemented yet
* d3c3eab HUE-6660 [optimizer] Limit the number of columns we send stats for
* 0e3ffef HUE-6656 [editor] Fix js error in the statement parser with open backticked identifiers
* db17ece HUE-6342 [autocomplete] Add to_timestamp and from_timestamp to the Impala function library
* 3ad78b7 HUE-6671 [editor] The metadata notifier should be aligned to the right snippet headers
* 752ca78 HUE-6666 [frontend] Improve sign in form
* 7ca155a HUE-6670 [oozie] Avoid double modal on bundle submission
* 999a7cd HUE-5739 [editor] Increase the min-width of the sql context popover to fit all tabs
* 1ad8678 HUE-6653 [assist] Fix issue where some of the last tables aren't shown in the assist for certain window heights
* 0249b3e HUE-6669 [editor] Improve fixed headers positioning on Hue 4
* ae3b8ed HUE-6651 [frontend] Prevent showing multiple error message with the same text
* 95325e8 HUE-6667 [frontend] Drop nicescroll from the main Hue 4 panel
* 4da2262 HUE-6668 [frontend] Disable caching of JS files for development
* 56db330 HUE-6580 [editor] Add DB prefix when fetching top tables
* 7a69223 HUE-6653 [assist] Improve initial height estimations for the assist foreachVisible bindings
* c9e43f7 HUE-6365 [assist] Tone the hover background color down in the left assist
* 2807e8a HUE-6653 [frontend] Make sure the foreachVisible binding updates visible entries in case the size changes
* c95a760 HUE-6658 [aws] Use region as a the default if both region and endpoint are undefined
* 1e6bcc0 HUE-6655 [autocomplete] Don't reset the autocompleter event handlers when the suggestions haven't changed
* 1cadc97 HUE-6654 [doc2] Do not fail import when document parent directory is null
* 48e270c HUE-6633 [core] Download logs as zip files should work on Hue 4
* 8f1cb34 HUE-6648 [editor] Fix statement type drop-down positioning
* 75a2d04 HUE-6582 [assist] Add DB prefix to tables in the right assistant
* cc0b4fb HUE-6646 [frontend] Don't show horizontal scroll bars in the Hue drop-down
* c63179b HUE-6645 [autocomplete] Suggest FROM after the select list
* 3950e7f HUE-6647 [frontend] Improve initial rendering of the log scroller binding
* f3622b4 HUE-6644 [frontend] Show file chooser Home breadcrumb in case of error too
* 6cffd12 HUE-6643 [frontend] Enable caching of Ajax calls when loading external files in Hue 4
* af3cfb5 HUE-6629 [core] Click on the main navbar username should close the mini JB and task list panels
* 024e6c3 HUE-6622 [jb] Avoid page freeze if the counters call returns zero results
* 4cd3d7b HUE-6624 [jb] Mini JB shouldn't have a border on the left side
* 1c00455 HUE-6641 [jb] Remove console.log messages
* d3c8668 HUE-6628 [core] Skip the current '.' folder from the S3 file picker
* 69a7d25 HUE-6631 [editor] Unify font usage in the snippet header
* 4c42f51 HUE-6630 [editor] Improve readability of the autocomplete function descriptions
* 7163eeb HUE-6632 [assist] Unify the context popover header and panel layout
* 924fe6b HUE-6620 [home] Fix jumpy breadcrumbs on hover
* 5d842ca HUE-6640 [home] Fix JS error on back
* 1575d55 HUE-6619 [frontend] Fix border radius on top bar search
* e49f856 HUE-6597 [assist] Add HDFS go home action to total storage
* 6e7fb4b HUE-6613 [frontend] Fix flex issues in IE 11
* ddb6089 HUE-6639 [assist] Fix issue where drop-downs are hidden behind flex panels in Hue 3
* 87d8858 HUE-6616 [home] Use global document type translations throughout
* 2abae65 [HUE-6636] Fix exit status for the ldaptest command when no LDAP parameters are given
* 6f98cfc HUE-6635 [core] Update translations files
* 82aaeac HUE-6634 [importer] Provide error to user when Sentry permissions are missing
* ee0e242 HUE-6546 [core] Automatically configure Hue Axes log the remote ip.
* fded00f HUE-6618 [optimizer] Show list of parsing error on table upload error
* f19e4d4 HUE-6617 [editor] Java example error on submission
* e167263 HUE-6616 [home] List english names of document types
* 9de07a4 HUE-6615 [editor] Fix multiline comment related issues with the statement parser
* c9d8c70 HUE-6615 [editor] Fix comment related issues with the statement parser
* de34729 HUE-6610 [frontend] Saving a query result as directory shouldn't throw a JS error
* 8eb8033 HUE-6611 [importer] A table with many columns is not rendered correctly on Hue 4
* daea239 HUE-6049 [frontend] Remove invalid HTML from the top navbar
* 8a64213 HUE-6596 [frontend] Avoid JS error on missing template switching from editor to other apps
* 233a03f HUE-6609 [frontend] Swap position initial to static to be IE compatible in Hue 4
* 4e080fd HUE-6608 [editor] The db dropdown throws a JS error on Hue 3
* b8a2fa3 HUE-6564 [indexer] New indexes not showing up and remove cache from assist
* 73ced05 HUE-6596 [editor] Load Editor then load Notebook does not load
* 03ac42e HUE-6592 [aws] Add more precise exception handling for AWS file handler
* e42dcfd HUE-6606 [notebook] Document selection does not filter by type
* 440b79f HUE-6599 [editor] Only add new logs when using Oozie batch connector
* 551ac92 HUE-6445 [editor] Parameterization without curly brackets not working in Pig editor
* ea57424 HUE-6603 [core] Bump version to 4.0
* 741d328 HUE-6602 [editor] Limit the availability history check to N last running queries
* b5f22c2 HUE-6601 [editor] Offer to add file in sqoop snippet to provide DB connectors
* 7f0bd68 HUE-6600 [dbms] Protect from 'ascii' codec can't encode characters in position
* 0e2fe12 HUE-6599 [editor] Slow down fetch status after 45s
* e64d660 HUE-6598 [jb] Clean-up the task attempt page
* 5fd5d11 HUE-6598 [jb] Clean-up schedule and bundle pages
* 4f28c81 HUE-6598 [jb] Add queue or group name to the job list
* c3f457e HUE-6607 [editor] Properly construct impalad coordinator URL
* 46fb141 HUE-6604 [oozie] Fix timestamp conversion to server timezone
* b56fe09 HUE-6593 [aws] Don't lowercase bucket names before looking up buckets
* f8195fa HUE-6594 [fb] Avoid TypeError on clicking on create folder without a name
* 6184628 HUE-6591 [editor] Only subscribe to upload query when optimizer is on
* 80f0289 HUE-6591 [metadata] Only upload query for SQL types
* 24eb6a1 HUE-6590 [jb] link-or-text should not error on non string data
* 51b8bb9 HUE-6590 [jb] Add Spark job details to the page
* ea075d5 HUE-6589 [jb] Fix progress percentage for MapReduce jobs
* 94a9efb HUE-6588 [jb] Adding default log display of the most important task attempt logs on main page
* 4674262 HUE-6587 [optimizer] Query risk statement format is not always a single line
* 9ea0e19 HUE-6586 [sqoop] Strip sqoop if present in beginning of command
* 665d81b HUE-6565 [search] Add tooltip to field names in grid list
* 7710217 HUE-6584 [assist] Clicking on HDFS and S3 filter icon does not focus in the filter input
* 923a144 HUE-6563 [editor] Filter out workflow history from task history
* e022826 HUE-6326 [core] Manually re-apply HUE-4403
* bba8cf2 HUE-6583 [security] Hashchange should respond on the exact security path
* 230f21d HUE-6579 [security] Hard reset the security app contents
* 1999d68 HUE-6579 [security] Resolve double binding on the Solr part
* 0b203aa HUE-6534 [home] Set the correct height of the elements to improve rendering of the docs list
* e74c3b6 HUE-6532 [assist] Add a document type filter to the assist documents panel
* 4e51667 HUE-6551 [editor] Improve the visibility of the active database
* 6e65066 HUE-6574 [autocomplete] Prevent the autocompleter from changing the case when the user types a complete suggestion
* 5af5b67 HUE-6574 [autocomplete] Improve autocompletion when typing complete suggestions
* e916829 HUE-6570 [editor] Improve the error message when the context popover can’t load a table
* 7869602 HUE-6568 [editor] Fix the column location marking
* ed47984 HUE-6577 [jb] Restyle variables on the job details page
* ba3c9b6 HUE-6578 [editor] Move row details modal to common footer
* 224f069 HUE-6576 [editor] Closing the result search does not remove the yellow highlighting
* 76f1280 HUE-6557 [frontend] The context panel should disappear when the editor loses focus on Hue 4
* 3d87ac6 HUE-6569 [core] Port missing styles to Share modal
* c17a513 HUE-6572 [frontend] Upload progress bar is a bit off in File Chooser
* e1e7091 HUE-6571 [frontend] Improve reliability of openInHue4 JS
* 70c37c4 HUE-6566 [frontend] Prevent JS error on empty URLs for open.link
* 7c5a42d HUE-6567 [frontend] Avoid JS error on multiple bindings opening a bundle editor after a schedule editor
* a02012f HUE-6558 [oozie] Add backdrop to bundle editor modal on Hue 4
* 919d304 HUE-6558 [oozie] Fix modal dialog message on bundle editor chooser
* b42f704 HUE-6558 [oozie] Fix modal dialog message on schedule editor chooser
* 39126ff HUE-6562 [optimizer] Upload 'num_partitions' as table stat
* 7c79d7a HUE-6561 [metadata] Leave time to read the DDL stats upload result
* 7c056e6 HUE-6560 [metastore] Add proper timestamp to the action tasks
* a84ba9c HUE-6083 [metastore] Convert drop partition action to a task
* 51ec0dd HUE-6412 [optimizer] Set caching to 1hour
* 34e49a6 HUE-6559 [fb] Enable Trash icon when Trash path exists
* 897e196 HUE-6550 [editor] Don’t show the row count column on top of the banner when scrolling
* 594255a HUE-6549 [editor] Fix title on expand row icon
* 9a16792 HUE-6549 [editor] Don’t close the context popover when closing a modal on top
* 8243b10 HUE-6549 [editor] Show the context popover behind any modals
* 01692f1 HUE-6529 [editor] Ignore case for databases when showing the SQL context popover
* f0c392c HUE-6548 [autocompleter] Don’t cache API responses with code 500 when status is 0
* 17371bf HUE-6556 [frontend] Filechooser should use a global modal
* 0404dba HUE-6256 [notebook] Disable fixed first column for results in the notebook view
* 513ced4 HUE-6554 [frontend] Put moment timezone in the common header to avoid multiple instances of it
* 810f388 HUE-6553 [frontend] Avoid redrawing of fixed headers if the editor size hasn't changed
* e3f2cba HUE-6552 [core] Cluster config triggers multiple subscriptions bindings on the assist
* 2f22d4f HUE-6524 [editor] Added refresh button to the saved queries panel
* c875509 HUE-6083 [metastore] Fix overview panel display on table click
* 546cdac HUE-6083 [metastore] Ko-ify drop partitions
* 5856f1a HUE-6083 [metastore] Got rid of invalid br tags
* 1681a3a HUE-6547 [frontend] Remove dotted outline in Firefox
* e29b141 HUE-6545 [impala] Sample popups does not have information for upper case tables
* 7f81429 HUE-6417 [editor] Make left grid hover border as dark as log panel one
* 8881033 HUE-6083 [metadata] Update test to look for content in json
* 7592b84 HUE-6543 [metastore] Dropping objects should reset the selection
* 69e46f7 HUE-6540 [importer] Create database errors and does not land on the new db page
* 7a1ced7 HUE-6541 [core] Update test tarballs to pick up the latest version
* eab7bbd HUE-6537 [core] Promote the first category of interpreter
* a00e409 HUE-6536 [editor] Old SQL Editor used by default if only beeswax is allowed for user
* 6e1fe35 HUE-6546 [core] Automatically configure Hue Account Lock to not use Load Balancer's IP
* cc62a43 HUE-6542 [core] Add configuration comment for Hue Account lock login_cooloff_time
* 8716338 HUE-6054 [home] Add restore button to trash page
* 26299a9 HUE-6511 [assist] Rename table/db refresh tooltip to just 'Refresh'
* 4252a58 HUE-6539 [aws] Update AWS config check to connect to endpoint and avoid region check
* 7b7b37b HUE-6517 [useradmin] Skip and log when LDAP user with invalid username attempts to login
* 427a5ab HUE-6532 [assist] Add missing styles for doc filter
* 0f93fc6 HUE-6532 [assist] Add filter to the docs assist panel
* 1ed601a HUE-6532 [assist] Fix the header actions in the documents panel
* 0613bb4 HUE-6533 [frontend] Add missing /notebook URL to Hue 4
* b632b85 HUE-6518 [useradmin] Switch to Hue 3 from the user admins page gives 404
* 338d518 HUE-6083 [metadata] Render /partitions page as metastore.mako
* 580ea14 HUE-6525 [editor] Hue 3 fullscreen results have a big white space on top
* 30787f0 HUE-6526 [fb] Consolidate file view pagination
* 1dc6e37 HUE-6507 [frontend] Style selected task on the task list
* 0ec1f8d HUE-6521 [metastore] Hue 3 table page has a small filter input
* 4765a34 HUE-6530 [jb] Bring back the expand button in the JB mini
* 31d3c7f HUE-6413 [editor] Deleting a rule in query builder throws a js error
* 183ab16 HUE-6522 [editor] Fix context popover for tables in the assistant panel
* f5c8271 HUE-6531 [metastore] Fix context popover in the megastore
* 8b7a218 HUE-6529 [autocomplete] Ignore case when comparing table identifiers and aliases
* 910a917 HUE-6499 [jb] Improve arrow rendering on the main JB page and remove graph from the JB mini
* 356b12f HUE-6509 [jb] Workflow tabs stop working in the main page if a mini jb is open
* f85e265 HUE-6528 [jb] Plug in readonly xml for for task page
* 36f7617 HUE-6516 [oozie] Turn back on document action
* 549f1b8 HUE-6514 [optimizer] Correctly load password from script when specified
* 2157c97 HUE-6515 [aws] Do not use a default region if not configured, fallback to standard S3 endpoint
* a966c48 HUE-6513 [optimizer] Rename config property to auth_key_id
* 5263bc7 HUE-6488 [oozie] Oozie workflow throws server error 500
* 17a780f HUE-6487 [aws] Bubble up errors on s3 mkdir
* 9ba07ea HUE-6326 [aws] Add support for new S3 regions
* 2aa3460 HUE-6466 [aws] Check S3 privileges for user before activating s3 filesystem
* 23b51d9 HUE-6370 [jobsub] Save jobsub doesn't redirect to list-designs page.
* 3f045ac HUE-6510 [jb] Fix JS error on coordinator and bundle pages
* 3be5bd7 HUE-6512 [frontend] If Hue is down, infinite loop on non page refresh when doing an action
* bfd7fb9 HUE-6367 [fb] Right click popup offset is off
* 0723b10 HUE-6458 [jb] Create a component to render HDFS links
* f98d629 HUE-6510 [jb] Styled metadata
* 4c61335 HUE-6510 [jb] Styled job counters
* 5ed2c67 HUE-6510 [jb] Style the job logs links and make logs scroll
* 93f1fef HUE-6495 [autocomplete] Update the Hive general UDFs
* 8f4a3a6 HUE-6495 [autocomplete] Add the Hive mask functions to the function library
* 16ac407 HUE-6495 [autocomplete] Add support for the Hive extract date function
* 167b02f HUE-6506 [importer] Fix scroll to bottom and reliability on Hue 4
* 274ee57 HUE-6508 [metastore] Fixed actions menu has the wrong offset in Hue 4
* 254507d HUE-6505 [metastore] Adding table names to drop task
* 065c75c HUE-6505 [metastore] Fix js error when clicking on refreshing DB tables
* 4eb5ce6 HUE-6504 [importer] Add error message when related to query compilation issue
* 8d292a8 HUE-6503 [search] Browse URL does not load the specified collection
* 5a88df1 HUE-6502 [indexer] Add current datetime to tasks submitted importer
* 85c1c93 HUe-6501 [oozie] Remove unused filtering on bundle page and style the border
* 2550b3a HUE-6501 [importer] Do not show index as a destination by default
* 876e801 HUE-6501 [oozie] Prevent opening coordinator action that has an invalid job id
* 465f86d HUE-6501 [oozie] Hide coordinator action filtering as not implemented yet
* d04b5da HUE-6501 [oozie] Properly list status color of coordinator actions
* 5557c56 HUE-6500 [editor] Provide Oozie logs when job logs are not available
* 0e9b54a HUE-6499 [oozie] Avoid infinite loop on workflow editor page
* f4a1fe6 HUE-6499 [oozie] Improve arrow rendering on Hue 4 workflows
* e44badb HUE-6495 [autocomplete] Update the Impala analytic functions
* 3374088 HUE-6495 [autocomplete] Update the Impala misc UDFs
* e61b6ba HUE-6495 [autocomplete] Update the Impala string UDFs
* 5330415 HUE-6495 [autocomplete] Update the Impala built-in conditional UDFs
* a751a4a HUE-6495 [autocomplete] Update the Impala built-in date UDFs
* 8c34fb1 HUE-6495 [autocomplete] Update the Impala built-in type conversion UDFs
* 78a9c75 HUE-6495 [autocomplete] Add the Impala bit functions to suggestions
* c9fd9bc HUE-6495 [autocomplete] Update the Impala built-in mathematical UDFs
* 26c89c5 HUE-6491 [autocomplete] Prevent logging of unknown chars to the console
* 47565b7 HUE-6077 [editor] Improve vertical positioning of queries in the query history table
* 23d4fc5 HUE-6498 [frontend] Restyle the history panel notification part
* 72b672b HUE-6497 [fb] Fix positioning of the context menu in Hue 4
* 8225f56 HUE-6496 [oozie] The bundle submit page should render normally in Hue 4
* 868ab2d HUE-6493 [editor] After saving query result to file, query editor page still shows the save dialog
* 6ef71d9 HUE-6492 [core] Avoid http 500 on null id document download
* 825f7a3 HUE-6490 [fb] Avoid multiple loading of Filebrowser paths
* 97795cf HUE-6489 [fb] Fix frontend pagination
* 21a9f4d HUE-6494 [assist] Avoid JS error on huePubSub assist.document.refresh
* 5bcdc5d HUE-6485 [frontend] Avoid jump on the left assist when opening Hue 4
* 5d29798 HUE-6484 [home] Some CSS styles are leaking into filebrowser
* 2b87ce0 HUE-6481 [frontend] Better error management on S3 file picker when the user doesn't have access to a bucket
* 38a02a0 HUE-6482 [frontend] Hue 4 should never open /home2
* a4726c1 HUE-6472 [assist] Functions dropdown is hidden under below flex panel
* fca053b HUE-6477 [frontend] Tighten null check on intervals and subscription utils
* fa7cfac HUE-6483 [frontend] Use the favourite editor as the sidebar editor link
* 8b63cdf HUE-6479 [frontend] Update the top nav create button when the favourite app has changed
* 8b15240 HUE-6478 [editor] Add multiple snippet support to the statement parser
* 5a91d31 HUE-6475 [assist] Toggle the right assist depending on the notebook contents
* 9eb9b1a HUE-6476 [assist] Fix assist in RDBMS
* 4dbb154 HUE-6475 [assist] Hide the right assist in the Hue 3 editor when empty
* ea6d870 HUE-6475 [assist] Only show the functions panel for Hive, Impala and Pig
* 65b3b34 HUE-6474 [editor] Show the right assist by default in Hue 3 editors
* ecc5d00 HUE-6473 [frontend] Move top banner into the main-page to prevent it from pushing the page down
* 258b6e1 HUE-6468 [frontend] Dropping an xls/json file to 'Drop files here' shouldn't redirect to importer
* 6148056 HUE-6470 [core] Adjust the z-index of the custom banner so the result table doesn't overlap
* 28aaf4b HUE-6471 [frontend] Rount the /jobsub urls on Hue 4 to Hue 3
* 79a673c HUE-6469 [search] Toggle auto-refresh on new dashboard page shouldn't error
* 335b62b HUE-6267 [pig] Skip Pig job submission tests if Hue 4 is enabled
* 19f9ae0 HUE-6446 [oozie] Fix can_edit_json parameter type
* 45e9e71 HUE-6465 [home] Properly load the editor when creating a new document from home
* e3a90b5 HUE-6464 [editor] Prevent transient js error when switching apps in pauseAppIntervals
* 27584a1 HUE-6428 [editor] Java type does not provide fields for arguments
* 31e3db4 HUE-6446 [oozie] User cant edit shared coordinator or bundle
* eca8e4f HUE-6461 [oozie] Series of hueLinks missing
* 40313a7 HUE-6245 [notebook] Adding is_sql properties to check interpreter tests
* b309d88 HUE-6245 [core] Typo where set preference should return it too
* cb6786e HUE-6462 [metastore] Location link can point to Hue 3 File Browser
* 509329f HUE-6461 [fb] Default batch archive extractor feature to false
* 7af1d31 HUE-6245 [hive] Use regular beeswax name as name of Hive connector
* e1ce077 HUE-6267 [editor] Add Spark Job Editor example for Hue 4
* 41cdb1b HUE-6267 [editor] Add PySpark Job Editor example for Hue 4
* 804eaa6 HUE-6267 [editor] Add Java Job Editor example for Hue 4
* 4968807 HUE-6267 [editor] Add MapReduce Job Editor example for Hue 4
* f2b4939 HUE-6267 [editor] Include pig editor script example
* 10c1219 HUE-4918 [importer] Invalidate Impala metadata on new table creation in Hive and Impala
* a7c22aa HUE-6459 [imporeter] Fix js error on task creation error
* 4a5dca9 HUE-6457 [fb] Avoid parsing of @ character on the hash path
* b79f3ed HUE-6460 [core] jHueNotify adds extra spaces when the notification is too fast
* e87fea8 HUE-6455 [frontend] Fix Ace require base path for the highlight and readonly XML bindings
* 523c4e1 HUE-6453 [oozie] Fix available actions JS error on workflow editor
* 0ee9274 HUE-6452 [core] Make Importer non cached on Hue 4
* b4498ba HUE-6456 [metastore] Silence metadata API error
* d2e1ccc HUE-6245 [metastore] Fix js error on load of the metastore page
* 5b5fd25 HUE-6454 [metastore] Fix issue with missing css in Hue 4
* 55686bb HUE-6444 [assist] Update the documents panel on any document modifications
* 392facf HUE-6451 [editor] Show qualified names for columns in the sql context popover title
* b4c3ee1 HUE-6451 [editor] Show qualified names for tables and views in the sql context popover title
* 5e9f126 HUE-6450 [frontend] Don’t close the main search on enter
* 3341e62 HUE-6449 [oozie] Select a workflow has a wrong z-index
* dc0322b HUE-6414 [frontend] Move Firefox scroll specific fix to one single element
* 681d5b9 HUE-6368 [importer] D&D to importer in menu no css effect on hover
* 854ed1a HUE-6448 [oozie] Edit coordinator/bundle page fails to load
* eee5c11 HUE-6356 [importer] Add proper hueLinks
* fa52178 HUE-6245 [cluster] Do not show the dropdown when no extra clusters are configured
* 6a64b83 HUE-6245 [metastore] Backward compatibility between beeswax and hive names
* 4347313 HUE-6245 [cluster] Remove cyclic dependency in notebook conf
* cff3ae6 HUE-6356 [importer] Add message when table name contains invalid characters
* 7d1222e HUE-6245 [cluster] Clean-up imports and hardcoded hive sources
* 2d27fe7 HUE-6245 [optimizer] Always run optimization checks via HS2 API
* f4c131d HUE-6245 [notebook] Properly show notebook separator only if it is configured
* 4f4482c HUE-6245 [oozie] Automatically show available action in workflow editor
* 0a45ae3 HUE-6245 [cluster] Do not show top interpreter divided when first is not notebook
* 40826eb HUE-6245 [cluster] Only show Job Browser if the cluster has a list of jobs
* c915ec2 HUE-6245 [cluster] Use constants for cluster types
* 7adae43 HUE-6355 [metastore] Removing hardcoded hive DB source in page refresh
* ca55bf1 HUE-6356 [importer] Make submission DB source and target generic
* a0a7965 HUE-6356 [importer] Use correct default SQL source for table destinations
* a47a80b HUE-6245 [core] Move get current cluster config logic to models
* b1f43e3 HUE-6355 [metastore] Parameterize the database type used to browse the tables
* cf9645d HUE-6245 [cluster] Refactor logic to be contained in the ClusterConfig class
* 4515d26 HUE-6245 [impala] Offer an Impala cluster only
* 91cfc67 HUE-6245 [jb] Switches list of Job browsers interpreter when switching clusters
* 74daa4b HUE-6245 [dataeng] Nicer error when canceling a pending submission
* 123ab74 HUE-2645 [dataeng] Update dataeng command to version 0.9
* b50c677 HUE-6245 [cluster] Move user cluster retrieval logic to a class
* 676f2e1 HUE-6245 [dataeng] Execute jobs via dataeng API when dataeng cluster is selected
* f93ff39 HUE-6245 [cluster] Persist currently selected cluster
* e95220a HUE-6245 [cluster] Load back persisted cluster
* a073596 HUE-6245 [cluster] Load the default or last used cluster
* dad1e7e HUE-6245 [cluster] Load cluster list from ini configuration
* 9a2a6bb HUE-6245 [cluster] Display list of cluster dynamically in the top menu
* 5cc2996 HUE-1176 [jb] Automatically update the list of apps available depending on selected cluster
* cf7c42e HUE-6245 [dataeng] Add a basic job page in the browser
* 3f6946f HUE-1176 [jb] Avoid error on SLA page
* 6ba6014 HUE-6245 [dataeng] Load a dataeng job in Job Browser
* f3a37ed HUE-6245 [dataeng] Integrate the API in the editor as a new interpreter
* 959557b HUE-6245 [dataeng] Implement API to submit and monitor batch jobs
* 76f8a3b HUE-6245 [cloud] Start ko-ifying the multi cluster dropdown and list dataeng clusters
* 43246ef HUE-6245 [cloud] Adding multi cluster configuration support
* 3fdb067 HUE-6245 [dataeng] Add list of jobs to Job Browser
* e7502e0 HUE-6245 [dataeng] Add list of clusters and jobs API
* 51afe6b HUE-6245 [dataeng] Adding initial submission and cluster listing API
* c9ed76d HUE-6095 [pig] Set is_hue_4 flag
* 04c1db1 HUE-6094 [jobsub] Set is_hue_4 flag
* 50be558 HUE-6094 [editor] Convert jobsub Java document types to new editor
* e534486 HUE-6094 [editor] Convert jobsub shell document types to new editor
* 2d437f2 HUE-6094 [editor] Convert jobsub mapreduce document types to new editor
* bd1897d HUE-2890 [doc] Fix typo in README.md packaging section
* 9113fa7 HUE-6407 [pig] Play button doesn't come back after killing the running pig job
* 220004e HUE-6442 [frontend] Improve IE11 autocomplete trick
* 41c4b8b HUE-6438 [jb] Fix merge error
* 59799b3 HUE-6438 [jb] Change all the details pages to look good on jb mini
* e7d20bd HUE-6438 [jb] Improve CSS for mini jobbrowser mode
* 8cf9b92 HUE-6433 [jb] Avoid js error when Pig script does not have any child job
* 13ceba4 HUE-6432 [home] Delete document modal document dependencies links point to Hue 3
* 6d10f55 HUE-6432 [oozie] Submission error not displayed
* 5fc0118 HUE-6427 [editor] Allow to select folders as source or destination of distcp
* 7b3509b HUE-6426 [importer] Parquet table are not created properly
* 7e907a9 HUE-6425 [editor] Bump autocomplete timeout
* e2b2e38 HUE-6412 [optimizer] Lower cache TTL to a few hours
* c27aeb2 HUE-6437 [editor] Make database list scroll with the page
* 76ddf18 HUE-6435 [oozie] Exclude action parameters from isDirty calculation
* 9ff10c7 HUE-4918 [assist] Mutually clear the Hive and Impala cache from the metastore and editor
* 9fa5343 HUE-6439 [metastore] Clear the client side cache when refreshing the metastore page
* 5dd9acc HUE-6440 [assist] Also clear the Impala cache when clearing all caches
* 71ce5f4 HUE-6436 [editor] Fix context popover file tree layout
* 4eebbaa HUE-6345 [home] Fix layout issues from the addition of description
* b86cfd0 HUE-6434 [assist] Open S3 files in the file browser on click
* f063570 HUE-6434 [assist] Open HDFS files in the file browser on click
* bb191d2 HUE-6424 [assist] Style the table list in the assistant
* a363ef1 HUE-6424 [assist] Show the context popover on hover for the assistant tables
* 38142e9 HUE-6421 [assist] Enable dnd and double click to insert from the functions panel
* 4f101e8 HUE-2890 [doc] Simplify Ubuntu package installs
* 2c01b9c  HUE-6412 [optimizer] Remove email parameter of get_tenant
* 0f0d7fd HUE-6080 [metadata] Re-apply avoid none casting in navopt lib versioner
* 755b850 HUE-6412 [optimizer] Update API for production
* ca1ff62 HUE-6412 [optimizer] Point to production API
* 4e5e616 HUE-6411 [home] Create a new dashboard goes to dashboard page that can go to Hue 3
* 1a5001f HUE-6410 [security] Links to tables and objects opens in Hue 3
* 753a547 HUE-6422 [editor] Bar Charts can be messy when user toggles the 'columns <' icon
* c37766c HUE-6420 [editor] The huePubSub subscribers should have a specific type to be paused correctly
* a87dc22 HUE-6378 [frontend] Search input on the filechooser is bigger than necessary
* c1eb4c0 HUE-6199 [core] Global scroll up anchor on Hue 4
* c62a448 HUE-6290 [editor] Remove scroll up if embedded
* 5396d10 HUE-6423 [editor] Fix the snippet database dropdown and jumpiness
* c61433d HUE-6414 [frontend] Scrollbars are missing on Firefox
* 24a36e1 HUE-6382 [frontend] Fix sidebar positioning when banner is present
* 8e892d1 HUE-6419 [frontend] Switch to three bars in the hamburger menu
* 18a5ba0 HUE-6418 [editor] Refresh the statement locations on execute
* d884621 HUE-6417 [editor] Make left grid hover border darker
* e8d8a91 HUE-6416 [fb] Opening an image file in sends back binary
* fcd404c HUE-6415 [search] Field analysis popup is opening with offset and not styled properly
* 1cf4334 HUE-6383 [jobsub] Fix failing tests
* 70aeb22 HUE-6397 [sentry] Add Sentry API connection check to config check
* 9798611 HUE-6400 [assist] Add page length and alpha order check to HDFS and S3 deep loading
* 0aca8da HUE-6406 [autocomplete] Don’t add alias to suggestions when already present
* 0fdeb59 HUE-6406 [autocomplete] Identify complex columns in the metadata results
* 1f130e2 HUE-6406 [autocomplete] Adjust the parser to report complex identifiers when suggesting columns
* 9574e20 HUE-6403 [editor] Show the correct context popover for complex types
* 2d163b0 HUE-6403 [autocomplete] Report complex locations as complex type and not column type
* 000ced0 HUE-6402 [editor] Prevent displaying an fa-times icon while the editor is loading
* 79f41ed HUE-6401 [assist] Prevent double init of the db panel if it’s the last opened one
* b358a53 HUE-6401 [assist] Remember the last opened panel in the left assist
* 6458ecb HUE-6400 [assist] Fix deep loading of S3 paths that has folders on subsequent pages
* ef8959c HUE-6400 [assist] Fix deep loading of HDFS paths that has folders on subsequent pages
* 09c3986 HUE-6405 [fb] Longer input field when editing breadcrumb path
* 9889b28 HUE-6404 [oozie] Workspace link should open File Browser in Hue 4
* 82e80d8 HUE-6399 [jb] Support job filtering for schedules and bundles
* 9f1e4fe HUE-6245 [optimizer] Upload stats with db prefix on table name
* 5768997 HUE-6245 [optimizer] Properly json decode the risk source platform
* 0929ff8 HUE-6395 [oozie] Avoid post submission event conflicts with other job types
* 0dee301 HUE-6395 [oozie] Bundle submittion should not redirect to Hue 3
* e94d17e HUE-6395 [oozie] Coordinator submittion should not redirect to Hue 3
* 206fd1a HUE-3285 [core] Adding example of HTML banner
* 2f6e5b8 HUE-6095 [editor] Remove redundant pig connector config
* 466a9f2 HUE-6383 [jobsub] Ignore parameters when key is empty
* 32c6912 HUE-6095 [editor] Import old Pig script to the new Editor
* 1b8ae04 HUE-6398 [jobsub] Fix loading edit design page
* 9eae6e1 HUE-6396 [home] Provide default name to JSON downloaded file if only Home directory is selected
* 7766b47 HUE-6160 [sentry] Default component value for Sentry v2 to hive
* d0fe728 HUE-6393 [oozie] Adding hueLinks to all quick view of coordinator and bundle dependencies
* 7afec42 HUE-6392 [oozie] Creating a new bundle should not redirect to Hue 3
* 85c35c2 HUE-6392 [oozie] Creating a new schedule should not redirect to Hue 3
* 1ab31af HUE-6394 [fb] Do not 404 when clicking on the app name link
* e5f80a4 HUE-6394 [indexer] Create collection is not styled and stays on blank page after submission
* fff7582 HUE-6380 [dashboard] Disable SQL dashboards by default
* 6a5d2fd HUE-6245 [cluster] Turn integrating scheduling and Impala action off
* dc2428f HUE-6245 [cluster] Correct tooltips for mini job browser
* eb39ab3 HUE-6380 [optimizer] Properly check if app is turned on or not
* 0e1da6e HUE-6380 [optimizer] Do not show SQL sample upload if app if off
* 0fe047a HUE-6375 [jobsub] Enable job submission snippets based on jobsub app status
* ab1a07b HUE-6390 [autocomplete] Enable popularity for complex column suggestions
* 46c68d4 HUE-6389 [autocomplete] Ignore subqueries when sending tables to the metadata API
* 596f286 HUE-6388 [assist] Remember the last open panel in the right assist
* 203b874 HUE-6388 [assist] Keep the left assist state when the panel visibility is toggled in Hue 4
* 8813ca5 HUE-6387 [assist] Add filter to the S3 panel
* 56fbb85 HUE-6387 [assist] Add filter to the HDFS panel
* 5844ed4 HUE-6387 [assist] Add home link in the HDFS panel
* 467b9e1 HUE-6387 [assist] Only show the active folder name in the assist breadcrumb for HDFS and S3
* 2005fc4 HUE-6386 [jb] Fix tooltip js errors caused by logs link listener
* ac74a63 HUE-6385 [frontend] Fix js error on foreachVisible disposal
* 6144772 HUE-6361 [editor] Fix active statement location in Impala
* dec5148 HUE-6384 [metadata] Fix upload table stats link
* 5da8483 HUE-6361 [editor] Only send the string of the active statement when executing a query
* 09a8c8e HUE-6361 [editor] Temporary statement format change until correct value is sent
* 4fd556d HUE-6381 [core] Validate character set of search field in desktop_documents2 table
* bdbff1f HUE-6379 [oozie] Add support for old oozie schemas in dashboard graph
* db00c2f HUE-3281 [core] Handle login test landing page with Hue 4
* db0e580 HUE-3281 [core] Turn on Hue 4 new interface by default
* e4f5f25 HUE-6375 [editor] Only list snippets which apps are enabled
* f09c8e6 HUE-6374 [useradmin] Style LDAP info link to not look like a button
* 4b5f48d HUE-6373 [impala] Inject table comment into the table API
* 3d6533f HUE-6361 [editor] Limit updates when cursor stays in the same statement and add throttle for change detection
* b93fed7 HUE-6361 [editor] Move remaining logic from assist to location handler and remove dead code
* 9278880 HUE-6361 [editor] Move gutter marker to the new Ace location handler
* 0ec3149 HUE-6361 [editor] Clean-up and centralize Ace editor location support into one module
* 5910ef7 HUE-6361 [editor] Add statement parser support for ; in quoted values
* 7187cab HUE-6361 [editor] Use the new statement parser to identify statement locations
* 45f8b87 HUE-6361 [editor] Create dedicated parser for SQL statements
* c7c4a8c HUE-6369 [jb] Port format_preserving_redirect to Hue 4
* e047cee HUE-6363 [importer] Creating a bew database and table links are not working
* 4a98588 HUE-6362 [frontend] Add more interpreter link should work and open
* 558a64a HUE-6353 [assist] Allow to open tables more than one time from the assist
* eafd85b HUE-6359 [editor] Shell and MR types are missing environment variable form fields
* 03374ff HUE-6358 [editor] Selector JS error for shell, mapreduce, etc types
* 3b4cb6a HUE-6357 [notebook] Enable the selection of queries from files, saved queries as snippet
* 289933c HUE-6334 [frontend] Add mention of staring default app in the welcome tour
* 851c731 HUE-6354 [impala] DESCRIBE DATABASE is now implemented
* f0b64b0 HUE-6352 [editor] Do not load twice the editor the first time
* 1b29785 HUE-6075 [oozie] Remove email body for schema 0.1
* a61bc08 HUE-6346 [home] Default sort to last modified time
* 564aae9 HUE-6345 [home] Add description to the document list
* a640707 HUE-6351 [assist] Keep the right assist state when closed
* da61b9d HUE-6077 [editor] Improve history table text alignment
* 0010274 HUE-6077 [assist] Increase the spacing after the assist search input
* 27ad62e HUE-6349 [assist] Show a spinner when uploading table stats
* cd80ec8 HUE-6348 [home] Fix jumpy header on hover
* 1b3fc57 HUE-6077 [home] Move styles to less, unify colours and extend browser flex support
* 807ae1d HUE-6340 [assist] Increase the stroke width of the documents icon
* 5f6b612 HUE-6160 [sentry] Refactor retry logic to ensure try-once round-robin, add tests
* 51ff2ca HUE-6343 [useradmin] User edit js notifification is only for Hue 3
* 578c3f7 HUE-6327 [aws] Fix filebrowser test that inspects scheme, catching any permissions errors
* 0d5d93e HUE-6269 [editor] "expected string or buffer" popup exception came back
* ff35dab HUE-6344 [optimizer] Refactor the tests to have only one DB for now
* 588dbb0 HUE-6344 [optimizer] Allow call on top tables without an input permission check
* 47a6e3e HUE-6344 [optimizer] Upload workload only once during the tests
* 4e9947a HUE-6343 [core] Mix of little polishing in useradmin and jobbrowser
* 9a681d1 [HUE-6233] Implement ldaptest Hue LDAP test management command.
* 8f8ecd1 HUE-6212 [oozie] Prevent XSS injection from packets
* 7cacdd9 HUE-6343 [useradmin] admin.css from indexer is conflicting into useradmin
* 284aaca HUE-6338 [editor] Rename a few Metastore to Table Browser
* 3bb192b HUE-6334 [frontend] Persist if Welcome tour has been seen at the DB level
* 23f0da9 HUE-6341 [frontend] Directly open documents from the main search
* 9ace227 HUE-6334 [frontend] Close tour on esc
* e13e9bd HUE-6334 [frontend] Add cancel link to the welcome tour
* 6906aae HUE-6083 [metastore] Enable filtering on the partitions tab of a table
* 5d28b79 HUE-6328 [frontend] Enable open in new tab from context menu on hueLinks
* 5282f94 HUE-6339 [assist] Enable scrolling in the assistant panel
* 278c674 HUE-6332 [frontend] The page title should mention the active app
* 0d72226 HUE-6340 [assist] Make the documents icon more like the fa icons
* 68de988 HUE-6077 [frontend] Remove specific upload button style from common-editor
* b1d846c HUE-6341 [frontend] Enable navigation from the top search autocomplete dropdown
* d76402e HUE-6340 [assist] Improved documents icon
* d333c75 HUE-6325 [jb] Remove pagination if it's loading jobs
* 09df16d HUE-6325 [jb] Create properties component
* 909bbfe HUE-6325 [jb] Moved duration and submitted for the workflow page to the left sidebar
* f54c3ca HUE-6325 [jb] Made logs scrollable
* 99be8cb HUE-6325 [jb] Harmonized job pages and breadcrumbs
* 783d908 HUE-6325 [jb] Harmonized right actions
* bafd37f HUE-6325 [jb] Converted types filter to Huecheckboxes
* 0755b64 HUE-6325 [jb] Removed states filter from the app detail page
* 9c8c9af HUE-6325 [jb] Removed binding error on states filter
* b835cc0 HUE-6334 [frontend] Create welcome tour for Hue 4
* 1390563 HUE-6338 [core] Rename all browsers in Hue 4 to have their simple names
* 359b32a HUE-6337 [dashboard] Broken page when there is no collection available
* b348999 HUE-6335 [optimizer] Strip newlines in test query to not fail at upload
* 833b181 HUE-6336 [optimizer] Cache tenant_id when not explicitly entered
* 360c0bc HUE-6335 [optimizer] Unify hue.ini settings with auth_key
* 81dce5c HUE-6335 [core] Add cluster_id property to the config
* b1bd150 HUE-6334 [frontend] Swap Bootstrap tour with Shepherd and create the Hue style for it
* 061a7fb HUE-6326 [aws] Update boto library to 2.46.1
* d44d11d HUE-6327 [aws] Support new regions and provide reasonable defaults for proxy configs
* af50391 HUE-6327 [aws] Support new regions and provide reasonable defaults for proxy configs
* 6801ba2 HUE-6130 [editor] Revert to have progress bar next to snippet handler line
* c2a4d95 HUE-6333 [core] Fix default app logic to properly loads non editors
* 3f5c972 HUE-6325 [jb] Reverted interval value
* 64c9b86 HUE-6325 [jb] Styled schedule page filter
* 669dba0 HUE-6325 [jb] Reload workflow graph on re-run
* a506a18 HUE-6325 [jb] Separated job and jobs interval variables
* b641361 [HUE-6243] Fix Hue Load Balancer SSL Handshake error
* 5b2a707 HUE-6325 [jb] Got rid of unused method
* 7e7160f HUE-6325 [jb] Avoid double loading of the jobs list at job browser opening
* 1f2127c HUE-6325 [jb] Get rid of double job browser counter polling on Hue 4
* 5421953 HUE-6325 [jb] Optimize arrows redrawing and visibility polling of the workflow graph
* 60a1801 HUE-6325 [jb] Specify jobbrowser in the app huePubSub.subscribers
* 1b40aac HUE-6325 [jb] Stop workflow graph refreshing when browsing away from it
* de9fca2 HUE-6331 [editor] Don’t show columns and tables with less than 5% popularity as popular
* 11fb867 HUE-6330 [autocomplete] Prevent propagation of the scroll event in the autocomplete dropdown
* 669cf20 HUE-6077 [frontend] Fix right panel toggle overlap with the scrollbar
* 1f2d5fe HUE-6329 [autocomplete] Fix popular filter weights
* b2fdf8a HUE-6328 [frontend] Add target attribute support to the hueLink binding
* cc1399e HUE-6077 [frontend] Add more space to the install examples list
* 786db85 HUE-6259 [core] Switching between Hue 3 and 4 preserves the current open app
* 536f14d HUE-6325 [oozie] Starting polishing of job page
* 396f23f HUE-6325 [oozie] Add quick log link to list of actions of a workflow
* 8076a22 HUE-6325 [oozie] Proper quick link to worklow action logs
* 8d54da4 HUE-6325 [oozie] Only show MR job name if it is different from its Id
* 0c59841 HUE-6325 [oozie] Adding properties to workflow action page
* 757abe0 HUE-6325 [oozie] Get friendlier breadcrumbs names
* fc652fa HUE-6325 [oozie] Add list of worklow variables and their links
* 5e39a77 HUE-6325 [oozie] Fix links pointing to query files on File Browser
* 0d2162c HUE-6325 [oozie] Adding link to optional saved workflow
* 1bdce2f HUE-6325 [jb] Add missing attributes to the new workflow page
* 9c3dff6 HUE-6323 [frontend] Specify on GA if the user is currently seeing Hue 4 or 3
* 99096dd HUE-6324 [core] do not check in checkAll plugin when there is no element
* 1534ccc HUE-6310 [doc2] [doc2] Create missing doc1 links for delete and copy operations
* 0a6f77f HUE-6312 [useradmin] Add error notifications on Hue 4 for sync ldap users/group modal
* 2da84eb HUE-6312 [useradmin] Add error notifications on Hue 4 for sync ldap group
* 59fe235 HUE-6312 [useradmin] Add error notifications on Hue 4 for sync ldap user
* 7573b99 HUE-6312 [useradmin] Add error notifications on Hue 4 for edit permission
* 16389c6 HUE-6312 [useradmin] Add error notifications on Hue 4 for edit group
* 68a98ff HUE-6312 [useradmin] Got rid of Routie on edit user
* 53f021c HUE-6312 [useradmin] Add error notifications on Hue 4 for edit user
* 98ca1ea HUE-6314 [metastore] Remove optimizer links
* fdd7575 HUE-6313 [editor] Listing queries from editor should list them
* a00a88d HUE-6322 [metadata] Support multiple tables in filter suggestions
* 1060fd0 HUE-6321 [metadata] Support multiple tables with aggregate function suggestions
* 1e93e4a HUE-6320 [editor] Enable context popover pinning for tables, views and columns
* 7d10305 HUE-6319 [editor] Fix autocomplete spinner positioning in Firefox
* 44b1c67 HUE-6318 [editor] Fail gracefully when the browser cache is full
* 265a441 HUE-6317 [editor] Fix the apihelper cache for metadata calls
* 4e9b467 HUE-6309 [editor] Enable Ctrl-p to go up a line in the Ace editor
* aebec51 HUE-5965 [sentry] Move delete privilege modal to the viewModel
* 6623a66 HUE-5965 [sentry] Fix binding call to the viewModel variable
* 6cd9830 HUE-5965 [sentry] Fix call to a private function
* b29bb24 HUE-5965 [sentry] Support hashchange without reloading the app
* 2252567 HUE-6316 [metastore] The sample table is not striped and the first column not aligned
* 21805de HUE-6315 [frontend] Avoid redirect to /500 on page error
* 98bee95 HUE-6298 [frontend] Add inactive-action class to the favorite app component icon
* a27ee88 HUE-6077 [frontend] Reduce top border size to 2px
* d86fb6f HUE-6312 [useradmin] Display errors from form submission
* c4dc3e6 HUE-6311 [home] Do not land on Hue 3 homepage in admin wizard
* 6fb62ce HUE-6248 [sentry] Enabling hash change after history fix was quite banal
* d801a8a HUE-6248 [sentry] Remove references to RoutieJS
* 6b8d63a HUE-6254 [jb] The widget and logs links shouldn't throw JS errors
* f7faa75 HUE-6077 [frontend] Fix history support for Hue 4
* 66c1f98 HUE-1176 [jb] Hide duration filtering in mini browser
* 38d9571 HUE-6305 [editor] Configure Hive interpreter even if Impala is not configured
* 2b8d58c HUE-6225 [metadata] Avoid string formatting error as variable is a list
* ead0d35 HUE-6308 [editor] Fix JS error when opening SQL popover for a table that has the same name as a database
* a1dcad6 HUE-6254 [jb] Allow refreshing of the job page
* ac6f863 HUE-6307 [frontend] Add middle click support for opening hue links in a new page
* eb6079c HUE-6306 [editor] Fix editor CSS for Safari
* ac64b96 HUE-6254 [jb] Add spinner to the graph loading
* b77cc2a HUE-6254 [jb] Fix the jobs links on Firefox
* 35a00dc HUE-6291 [frontend] Remove multiple loading of scheduler files
* 369864d HUE-6294 [editor] Opening saved query removes the pagination buttons
* f553397 HUE-6296 [optimizer] Properly skip query history who did not compile
* 4e23f53 HUE-6296 [optimizer] Upload past query history as example
* 8d80a9b HUE-6255 [notebook] Prevent multiple autocomplete dropdown to show in the notebook
* 1ce0828 HUE-6303 [editor] Fix metastore link in editor sql context popover
* b47a9af HUE-6302 [editor] Fix JS error on enter in db selection
* 2117637 HUE-6301 [autocomplete] Improve filter suggestions around AND and OR
* d5b307b HUE-6304 [editor] Make editor font size configurable on the options panel
* 253c6ba HUE-6077 [frontend] Restyled the Ace settings slideout
* 1cf7d31 HUE-6299 [home] Empty trash context menu should show up just when in trash
* 8a01ffb HUE-6160 [libsentry] Simplify HA retry logic
* 2e0df2c HUE-6248 [sentry] Remember the current app path in Hue 4
* 61af662 HUE-6248 [sentry] Avoid leaking of the same name functions in Hue 4
* bba3517 HUE-6248 [sentry] Avoid leaking of the viewModel variable in Hue 4
* d0708f9 HUE-6077 [frontend] Improve layout of the admin wizard page
* e2ee08f HUE-5853 [oozie] Check for the existence of the canvas when updating its position
* f1a300b HUE-6077 [frontend] Re-introduce striped background for HueDatatables
* d483208 HUE-6077 [frontend] Moved blue border to the top of the main navbar
* e1e10c3 HUE-6298 [frontend] Create a star application component
* 74dcd8b HUE-6257 [home] Last Modified timestamp gets updated when a file is moved to a different folder
* ce7b0a8 HUE-6077 [frontend] Set the minimum height for workflow widgets
* 985c6ed HUE-6297 [oozie] The widget expand shouldn't offset when the page has scrolled in Hue 4
* 3c95d8a HUE-6077 [frontend] The oozie parameters labels should be smaller
* e4d86ef HUE-6077 [frontend] Fix oozie logs icon on JB2
* 99f4e84 HUE-6281 [editor] Set a default size for the query name and description
* 7f46196 HUE-6241 [useradmin] Add/sync an LDAP users/groups in Hue 4 behaves correctly
* 4885319 HUE-6241 [useradmin] Add/sync an LDAP user in Hue 4 behaves correctly
* bf92e91 HUE-6241 [useradmin] Add a notification on user, group and permission change
* c03e378 HUE-6241 [useradmin] Modify a permission in Hue 4 behaves correctly
* 79ac641 HUE-6241 [useradmin] Delete a group in Hue 4 behaves correctly
* e1c78b9 HUE-6241 [useradmin] Add and modify a group in Hue 4 behaves correctly
* 5e03ede HUE-6241 [useradmin] The checkboxes on user and group lists should work after a Hue 4 redirect too
* ceafa01 HUE-6241 [useradmin] Delete a user in Hue 4 behaves correctly
* 19f6907 HUE-6241 [useradmin] Add and modify a user in Hue 4 behaves correctly
* 49ca861 HUE-6248 [sentry] Fixed the apply bindings for hive, hdfs and the common page
* ec82233 HUE-6296 [editor] Automatically upload query on the fly if enabled
* 4bf1a66 HUE-6293 [oozie] Integrate links with Hue 4
* 7c3af85 HUE-6293 [oozie] Submit a workflow should not open Hue 3
* 4152934 HUE-6292 [oozie] Properly prompt for parameters in document actions
* 59402b8 HUE-6295 [doc2] Avoid unrelated DB calls in sync_documents after import
* 3441d42 HUE-6226 [editor] Select * autocomplete UX improvements
* ab7be70 HUE-6160 [libsentry] Parse host and port from sentry-site rpc-addresses
* e86b312 HUE-6269 [editor] Getting sometimes "expected string or buffer" popup exception
* 4597123 HUE-6077 [frontend] Fix collectstatic error on context menu font missing
* d3e556f HUE-6077 [oozie] Fix header positioning
* 74325d1 HUE-6277 [assist] Avoid right panel tabs to overlap
* 8cde1ff HUE-6077 [frontend] Fix oozie logs icon
* df6f809 HUE-6276 [assist] Dragging from a database to editor should display the database name
* dce13db HUE-6281 [editor] Avoid the query title and description to go to a new line
* 3d49180 HUE-6282 [frontend] The sharing modal shouldn't scroll on dropdown open
* eaaff7e HUE-6283 [editor] Draggin a file to the editor should open it instead of redirecting to the file itself
* 68169f8 HUE-6284 [editor] Re-render the fixed results header and column at page focus
* ae8d95d HUE-6285 [frontend] Clearing history from popup after create table creates overlapping dialogs which are not clickable
* b56b4d0 HUE-6286 [frontend] Clicking “execute and watch” on Task history popup showing JS error
* 38a6bff HUE-6287 [frontend] Close mini job browser panel when clicking outside it
* 6f270b3 HUE-6280 [frontend] Sample data view is not aligned properly
* 399e443 HUE-1176 [jb] Harmonize fields of job listing
* 3ed81af HUE-6275 [oozie] Add kerberos support to Impala action
* a261a1b HUE-6260 [core] Do not leak user preference in IS_HUE_4 global variable
* bd7b68f HUE-6249 [optimizer] Track user performing API calls
* 09fc112 HUE-6249 [optimizer] Properly set the startingToken if specified
* 3bf577d HUE-6249 [optimizer] Support Sentry filtering on topAgg
* bde6541 HUE-6249 [optimizer] Support Sentry filtering on topFilters
* 20caac2 HUE-6249 [optimizer] Support Sentry filtering on topDatabases
* 2373956 HUE-6249 [optimizer] Support Sentry filtering on topJoins
* cfd5e1b HUE-6249 [optimizer] Support Sentry filtering on topColumns
* 83e7bcc HUE-6274 [metadata] Add flag to enable file search
* ce3d1de HUE-6077 [editor] Improve risk alerting messages
* 306ccbe HUE-6266 [converter] Remove unnecessary call to document link
* 7d0f783 HUE-6273 [oozie] Point app name to correct dashboard URL
* a93404c HUE-6268 [metastore] Import table data button is misaligned
* 1949908 HUE-6271 [metastore] The partition page has misaligned breadcrumbs
* 3b4c669 HUE-6077 [frontend] Add .map files required by Safari
* c5bb491 HUE-6270 [editor] Integrated scheduler sometimes gets a coordinator UUID that does not exist
* d8ad134 HUE-6264 [converter] Fix variable name typo
* 95501b7 HUE-6265 [home] Offer top document search even if metadata search if not available
* 3a850ea HUE-6265 [home] Do not conflict document filtering type when not on home
* 0b53f8c HUE-6249 [optimizer] Adding Sentry filtering on API arguments
* bc1a3fe HUE-6263 [converter] Delete Doc2 object incase of exception
* d66f6fb HUE-6264 [converter] Decrease memory usage for users with very high document1 objects
* b44d107 HUE-6077 [frontend] jHueRowSelector should publish an open.link event on Hue 4
* f9b1b60 HUE-6077 [frontend] Disable popstate listening on page.js to co-exist with Routie
* 6673723 HUE-6241 [useradmin] Fix permission editing cancel button path
* bd7b5b7 HUE-6241 [useradmin] Fix group editing cancel button path
* 083687d HUE-6241 [useradmin] Add sync ldap groups page to Hue 4
* bc667ed HUE-6259 [core] Load back user specific Hue version
* c451be7 HUE-6077 [frontend] Fixed spacing for the user menus
* 6a92439 HUE-6262 [core] Converter should separate history docs from saved docs
* ac2cb89 HUE-6261 [oozie] Avoid JS error preventing workflow action status update
* 7451a67 HUE-6245 [frontend] Only show main button when there is only one app
* 85b8bc2 HUE-6260 [frontend] Properly link to user profile in Hue 4 menu
* eeb3682 HUE-6077 [frontend] Remove console.log from Routie
* f7e2260 HUE-6259 [core] Add a version switch between Hue 3 and 4
* bea75e2 HUE-6254 [jb] Added spinner to the interface loading
* 7fcdbbb HUE-6254 [jb] Initial restructure of the Spark page
* 33bd7b6 HUE-6254 [jb] Initial restructure of the Impala page
* 20cb7a5 HUE-6254 [jb] Open job details inside mini jb
* c7ace1e HUE-6254 [jb] Initial restructure of the Mapreduce task attempt page
* 43d335a HUE-6254 [jb] Initial restructure of the Mapreduce task page
* fddeb34 HUE-6254 [jb] Initial restructure of the Mapreduce page
* 674ec7a HUE-6254 [jb] Initial restructure of the YARN page
* 1593260 HUE-6254 [jb] Initial restructure of the bundle page
* 5578fca HUE-6254 [jb] Initial restructure of the schedule page
* 2de7ac3 HUE-6254 [jb] Initial restructure of the workflow task page
* 7bdacdb HUE-6254 [jb] Initial restructure of the workflow page
* 766b9e7 HUE-6254 [jb] Removed status circle from the job list
* a617a0e HUE-6254 [jb] Restyled the mini JB list of jobs
* fc4b56f HUE-6254 [jb] The jobbrowser mini should open the details of a job in the main jb app
* cbd8ebb HUE-6205 [editor] Load integrated scheduler when opening query
* 10d7597 HUE-6264 [hive] Refactor and componentize multiple Tez session logic
* 7b94e04 HUE-6077 [editor] Do not leave query hint spinner spin forever if failure
* b39712e HUE-6254 [jb] Fixed workflow graph display
* bb735fd HUE-6254 [jb] Close JB mini when clicking on the main jobs button
* 70dc67b HUE-6254 [jb] Set jobs as default interface for JB mini
* 71e4ff2 HUE-6254 [jb] Mini jobbrowser is bigger now
* 1d37f98 HUE-6254 [jb] The mini jobbrowser doesn't respond or change the location hash anymore
* 52222ab HUE-6250 [frontend] Losing # fragment of full URL on login redirect
* 47850e8 HUE-6077 [metadata] Continue to improve the tests with joins
* c648579 HUE-6077 [metadata] Correct typo on noDDL stats
* 30aa745 HUE-6249 [metadata] Support Sentry filtering on query hints and popular values
* 5801691 HUE-6077 [metadata] Improve test coverage on missing tables and ddl stats
* 9e96e53 HUE-6253 [oozie] A newly saved workflow should pass its uuid to the sharing modal
* d15a7b1 HUE-6253 [oozie] Sharing a newly saved workflow can result in JSON decode error
* 523b324 HUE-6251 [editor] Log warnings and continue on failed bulk delete and copy actions
* f966ed6 HUE-6274 [core] Listen to hashchange events on the current active app only
* 7abd93b HUE-6248 [sentry] Fix series of links to open correctly in either Hue 3 or Hue 4
* 68345a1 HUE-6246 [assist] Added right context menu to S3 browser
* 77649b9 HUE-6246 [assist] Added right icon to file browser context menu
* 34ef943 HUE-6246 [assist] Added right context menu to collections
* d91b372 HUE-6246 [assist] Added right context menu to HBase and fixed open for Documents
* 62e0d42 HUE-6077 [frontend] Assist gray effect now covers the whole row until the assist right border
* be4d3cf HUE-6077 [frontend] Removed caret for jobs and inverted order of badge and icon
* 390f4ef HUE-6077 [frontend] Remove expand icon from the mini job browser
* dcad7b8 HUE-6077 [frontend] Split the jobs button in two parts and make the user caret disappear
* 8966159 HUE-6077 [frontend] Rename 'browse' to 'browsers'
* 315129c HUE-6244 [home] Menu simplification
* ffd82e7 HUE-6242 [home] Keep the optional document filter get parameter while browsing
* 427d83d HUE-6242 [home] Saved documents in Oozie point to filtered list of documents in home
* 834e196  HUE-6242 [home] Saved documents in Dashboard point to filtered list of documents in home
* 975a7a1 HUE-6242 [home] Saved documents in Editor point to filtered list of documents in home
* 2470301 HUE-6242 [home] Actually perform document type filtering
* 1a84794 HUE-6077 [editor] Add more test coverage on false positive hints
* c5bcc73 HUE-6241 [useradmin] Support operations in Hue 4
* fae07bb [editor] Submit schedule from integrated scheduler panel
* 2611094 HUE-1176 [jb] Add kill to schedules and bundles
* 3dfefc3 HUE-1176 [jb] Add ignore action of coordinator actions
* bf3e3f0 HUE-1176 [jb] Add rerun action of coordinator actions
* 27d6ba6 HUE-1176 [jb] Add rerun action of workflows
* e69d579 HUE-6227 [editor] Drag & Dropping tables could be DB prefixed
* de17c48 HUE-6239 [assist] Assist headers should have the same information in the title
* e02e31d HUE-6077 [frontend] More subtle assist hover effect
* 0137d7c HUE-6240 [core] Replace jHueTour with Bootstrap tour
* 69adbab HUE-6237 [editor] Avoid blinking of the result headers on paste
* 171aff2 HUE-6077 [editor] Simplify top risk alert message
* eade846 HUE-6077 [frontend] Add route fro logs download
* b85f6cd HUE-1176 [jb] Proper filtering of tasks of YARN jobs
* b852862 HUE-6077 [editor] Simplify listing of db.table in autocomplete for column
* 1b696db HUE-6077 [editor] Inform when suggestions are missing DDL or stats
* 928a779 HUE-6236 [core] Add expand icon to the table extender fixed first column
* 79032fe HUE-6235 [core] Fix table extender fixed cell and first column header DOM
* 7bb6420 HUE-6077 [frontend] Add table styles to the search row details
* a119fb6 HUE-6077 [frontend] Lighten up the side bar
* 7a9d092 HUE-6077 [frontend] Removed all references to table-striped
* e9e6e72 HUE-6077 [frontend] Improve left margin on the editor snippet
* 3946dfd HUE-6130 [editor] Running query progress bar color conflicting a bit with long gray bar separator position
* 2441a5f HUE-6234 [core] Log search does not display anything
* fdcb811 HUE-1176 [jb] Only show Oozie Configuration in non mini mode
* c922bc6 HUE-1176 [jb] Default to first interface in case there is no hash on page load
* e09baa9 HUE-1176 [jb] Move interface availability checking logic to re-use existing one
* d86ee1e HUE-6212 [oozie] Prevent XSS injection in coordinator cron frequency field
* 844b399 HUE-1176 [jb] Avoid displaying interface section in the breadcrumbs
* 79e3b25 HUE-1176 [jb] Filter and perform action on coordinator actions
* 777d8f4 HUE-6077 [frontend] Fix reloading of a specific Job
* 43bfc29 HUE-6077 [frontend] Fixed column selected css
* 07d360c HUE-2137 [search] Avoid bucket conflict when we have more than one
* a6df470 HUE-6231 [oozie] Coordinator editor crontab help link is dead
* d036de4 HUE-1176 [jb] Properly list coordinators and bundles
* a6dd1d5 HUE-1176 [jb] Properly get the app state for YARN jobs
* 94ff4db HUE-6228 [core] Disable touchscreen detection on Nicescroll
* 94ed7f5 HUE-6202 [editor] Update the right assistant when navigating using the keyboard
* f850097 HUE-6230 [metadata] Send unique tables to navopt
* bfb92fe HUE-6077 [frontend] Improve the styling of the sidebar
* 1a366b7 HUE-6077 [frontend] Open the first available interface by default
* 9fc514f HUE-6229 [metadata] Fix issue with nav opt params for tables that have the same name as databases
* 358212e HUE-6077 [frontend] Remove inset box shadow from the progress bars
* cd4b045 HUE-6077 [frontend] Simplify the column analysis table style
* 202192a HUE-6077 [frontend] Fix top padding of the collections page
* 950af4f HUE-6225 [metadata] Add logging information when listing nav cluster sources
* a1369fd HUE-6077 [search] Properly support browsing an existing collection
* 341b02e HUE-6204 [importer] Create table link loads the indexer
* 3529c41 HUE-6137 [core] Add audit events for export and download
* 81e6db4 HUE-6160 [libsentry] Cache Sentry client and update tests to include api2
* edb28fc HUE-6160 [sentry] Support Sentry HA with failover
* 4b7cc96 HUE-6077 [editor] Increase scroll distance for closing the autocomplete dropdown
* 4ff0ffa HUE-6077 [frontend] Fixed suggestion title white space wrap
* d225c95 HUE-6077 [frontend] Fix alignment of validation result
* d2decea HUE-6077 [frontend] Improve risk styling
* 62bdb99 HUE-6077 [frontend] Fixed some red colors
* cbcb79a HUE-6077 [frontend] Lighter ace error line
* ee4036a HUE-6077 [frontend] Removed gradient from the editor error messages
* bb12f37 HUE-6077 [frontend] Removed inner style from the assist sort dropdown
* 132b738 HUE-6077 [frontend] Fixed Ace gutter error style
* d8eb632 HUE-6223 [autocomplete] Fix issue where tables from subsequent statements appear in the autocomplete results
* f568d82 HUE-6220 [assist] Fix js error on disposal
* b011aa5 HUE-6670 [editor] Show neutral hint in case of parsing error
* bb65f9b HUE-6670 [editor] Avoid js error when hints recommendation switches
* afd6bf8 HUE-6222 [assist] Restyle sort filter
* e9f7bf6 HUE-6218 [editor] Fix JS error on spinner binding
* 8d246ac HUE-6221 [assist] Remove active from the filter bar
* 80ad627 HUE-6218 [editor] Improve CPU usage by hiding fa-spin and active
* 127a139 HUE-6218 [core] Decrease GPU usage of progress bars
* 40a9183 HUE-6219 [editor] Mark the active statement in the gutter
* 4793c9f HUE-6216 [editor] Fix js error in MS Edge
* 19d9597 HUE-6077 [frontend] Improve hover effects for the result table
* e0104ce HUE-6077 [frontend] Put top-nav below modals etc.
* 0c5e23e HUE-6215 [core] PopupException should be displayed and not redirected as a 500
* adc21be HUE-6215 [core] Make error and popup error embeddable
* 254587a HUE-6214 [editor] Vertically resizing the log section is flaky
* 1e9443d HUE-6213 [editor] Link to Impalad daemon can have a wrong https prefix
* 1d34d2b HUE-6077 [editor] Show feedback on query hint computation and error
* 471a931 HUE-6077 [frontend] Fix hue datatable default row height
* e1627ec HUE-6077 [frontend] Override table headers for sorting and fixed malformed FB dom
* 924bde9 HUE-1176 [jb] Add Proper logs and counter on the YARN task attempt page
* 2fd628d HUE-1176 [jb] Offer to filter map reduce tasks by status
* 7db098b HUE-6077 [editor] Reset the history if the type of the editor changed
* 3b5c9e6 HUE-1176 [jb] Add filter on map or reduce status on task page
* 98a4086  HUE-1176 [jb] Offer to filter YARN job tasks by name
* 83d5f43 HUE-6077 [frontend] Got rid of loader on fileviewer and fixed colors of the file area
* 729078a HUE-6077 [frontend] Moved top bar specific styles to cui-override
* 42d2a7a HUE-6202 [assist] Fix js error from fetching locations
* cc79224 HUE-6210 [editor] Fix js error on dispose of ko subscription
* 0d22a4f HUE-6152 [impala] If result count is 1024, append a +
* 312fc02 HUE-6077 [frontend] Rewrite file display height calculator
* ff0bf76 HUE-6209 [fb] Click on previous page on the file viewer shouldn't throw a JS error
* 15e1732 HUE-6202 [editor] Add pubsub to get the statement at the active cursor position
* 046fe4d HUE-6205 [editor] Move the integrated scheduler to the right assist panel
* 0d0afae HUE-6196 [assist] Remove the assistant from the Hue 3 context panel
* 0469d0d HUE-6202 [editor] Improve multi-statement location reporting
* 2729065 HUE-6207 [editor] Avoid to always show the horizontal scroll bar when there's no scrolling needed
* f9a1746 HUE-6208 [core] The scroll left anchor should reset the horizontal scrollbar position
* 97b6acb HUE-6077 [frontend] Moved border to top nav, removed inset shadow
* 90460ef HUE-6077 [frontend] Give more margin to the editor snippets
* 34541e7 HUE-6206 [editor] Support full screen results on Hue 4
* cb40810 HUE-1176 [jb] Proper tab switching on the bundle page
* 14f6957 HUE-6077 [frontend] Remove HTML validation errors
* ba48903 HUE-6077 [metadata] Add API response id for tracking
* 500429a HUE-1176 [jb] Add proper fields to the bundle page
* d879ce6 HUE-6162 [core] Don’t show LB warning message when Hue is accessed from a LB-host
* 1dd8fee HUE-3890 [editor] Creating a new query should not reset the tab to query history when on saved query tab
* c4e25f4  HUE-1176 [jb] Add bundle page and its actions
* c2b4008 HUE-1176 [jb] Add job actions to schedules and bundles
* 23611a5 HUE-6198 [editor] The result spotlight shouldn't leak on the other pages
* ebbdc25 HUE-6077 [metadata] Update risk analysis tests to use a db name
* 51aafc2 HUE-6201 [autocomplete] Fix location type for complex columns
* 5c523ae HUE-6200 [assist] First iteration of improved look and feel for the assistant panel
* e91f166 HUE-6077 [frontend] Process less on start of grunt watch
* aa7e4a9 HUE-6196 [assist] Add the right assist panel to the Hue 3 editors
* ade4595 HUE-6196 [assist] Add right panel support to the splitdraggable binding
* 1464d5a HUE-6196 [assist] Extract the right assist panel to a ko component
* e8b6967 HUE-6195 [assist] Fix issue with missing active facet in the assist table filter
* f818450 HUE-6194 [assist] Bind active tables to the correct source type
* f7dfd28 HUE-6077 [frontend] Remove double top border from sortable tables
* f31a62d HUE-5964 [useradmin] Port edit permission page to Hue 4
* 7fde2ee HUE-5964 [useradmin] Port edit group page to Hue 4
* ac2de54 HUE-5964 [useradmin] Port new group page to Hue 4
* 2f8e9fe HUE-6197 [impala] Fix XSS Vulnerability in the old editors' error messages
* 113a1ff HUE-6077 [editor] Started refactoring of query hints in assistant
* dd434f0 HUE-1176 [core] Rename user preference API url to be more intuitive
* b584e21 HUE-1176 [jb] Improve logic to support single dashboard action
* 6574562 HUE-1176 [jb] Allow to customize the landing page / main button default action
* 66f6383 HUE-1176 [jb] Land on same page as main action
* f214da3 HUE-1176 [jb] Automatically display YARN and/or Oozie jobs if app configured
* 048e797 HUE-1176 [jb] Show job browser when app is available
* 717492a HUE-6077 [metadata] Avoid empty NavOpt client in the test
* 098970f HUE-6077 [frontend] Start to restyle JB2
* 6c221f4 HUE-6193 [converter] Retain last_executed time when creating doc2 object
* f95fca4 HUE-6077 [frontend] Fixed no matches message on Search field list
* 5f0a8ca HUE-6077 [frontend] Fixed toolbar height on search matches the assist header height
* 983004d HUE-5967 [search] Show the field list just for resultset chart widgets
* 47b8b81 HUE-6077 [metadata] Add proper metadata information to the query upload
* 512584d HUE-6077 [metadata] Upload history query in a single line format
* e69fc94 HUE-5967 [search] Correct header padding for Hue 3
* 9710612 HUE-5967 [search] List of dashboards should redirect to home
* 51ec40a HUE-5967 [search] Fixed top bar styling for Hue 4
* 95c07d0 HUE-6077 [frontend] Move the jHueAutocomplete CSS to a LESS component
* cc9b573 HUE-6192 [editor] Fix a typo in the default interpreter list
* 93d9d78 HUE-6077 [frontend] Fix metastore scrollable issues on Hue 4
* b9a6e1b HUE-6077 [frontend] Fix breadcrumbs for Metastore and remove CSS leak
* c646b5b HUE-6005 [librdbms] Col details is empty for other than Hive and Impala
* 245204b HUE 5653 [jb] Complete implementation of Spark Job History Server REST API
* dbdb416 HUE-6077 [metadata] Use the proper statement of a query when uploading stats
* 0deb24f HUE-6077 [jb] Re-sort YARN jobs as they don't come sorted from API
* b6df1c7 HUE-6180 [beeswax] Extend _verify_query_state in beeswax tests to allow for multiple states (#514)
* 23239de HUE-6190 [editor] Default interpreter list should provide a list when using extend
* f0f0021 HUE-6189 [autocomplete] Make sure we always have table references for column locations
* eb8e600 HUE-6188 [editor] Only convert table locations to complex type when a database reference was found
* a469210 HUE-6077 [frontend] Fix alert close button alignment
* 78ef77b HUE-6077 [jb] List youngest YARN jobs first
* 61ecb59 HUE-6187 [useradmin] Support unicode characters in usernames
* a0477b0 HUE-6077 [frontend] Style the file browser breadcrumbs
* c1fe83f HUE-6077 [editor] Open YARN jobs of queries directly into Job Browser2
* 837ac84 HUE-6077 [frontend] Style table list on the assistant panel
* 9279532 HUE-6077 [frontend] Restyle a bit the create button
* 8ecb811 HUE-6077 [frontend] Get rid of fileChooserBtn height on all the apps
* 1181f6f HUE-5853 [oozie] Avoid dashboards to break after the workflow editor
* 16004da HUE-6077 [metastore] Rename Metastore Manager to Table Browser
* 56cb9b3 HUE-6077 [frontend] Put session-config css cross version
* 90ef766 HUE-6077 [frontend] Removed horizontal scrolling from Oozie
* f3c0532 HUE-6077 [frontend] Made scrollbars darker on Windows
* bfb8d9e HUE-6077 [frontend] Pretty nav-pills on the right panel
* 523efa3 HUE-6077 [frontend] Publish a nicescroll resize on app change
* 00a31d1 HUE-5853 [oozie] Added info panel to the new job browser
* 1d02191 HUE-6077 [frontend] Fix Java icon in the query dropdown menu
* 4da7b48 HUE-5967 [search] Remove fullscreen in Hue4 and fix url change
* 98006ea HUE-5967 [search] Fix toolbar zoom and remove horizontal scrolling in Hue 4
* 095a74b HUE-6185 [frontend] Properly dispose the ace editor and the autocompleter
* d992fd18  HUE-6184 [frontend] Allow ctrl/cmd + click to open Hue 4 links in a new tab
* cce8623 HUE-6077 [frontend] Fix the indexes header
* 192bc29 HUE-6183 [hbase] Fix issue where the page function is overwritten in HBase
* 3f4a226 HUE-6182 [frontend] Add default pages for editor and scheduler
* 6625d22 HUE-6182 [frontend] Switch to pubsub for cluster configuration
* db6858c HUE-6182 [frontend] Fix the assist initialization in Hue 3 pages
* 5dce002 HUE-6181 [sentry] Fix scope for privilege checker test
* 0a5e45f HUE-6176 [frontend] Load the left menu properly from the cluster config
* 8f19d93 HUE-6161 [doc2] Move document conversion migration from desktop to useradmin
* 2f911e3 HUE-6077 [frontend] Add a message to the login page
* 8044d83 HUE-5853 [oozie] Make info page embeddable
* e62eda1 HUE-5853 [oozie] Make SLAs page embeddable
* bc3cc0f HUE-5853 [frontend] Route the oozie document lists to Home
* ca53b8a HUE-6179 [frontend] Fix dom disposal for nicescroll and create a resize subscriber
* ec925a2 HUE-6077 [frontend] More padding for the create button
* 3c16cca HUE-6077 [frontend] Add padding to the right panel content
* ef847d2 HUE-6077 [frontend] Harmonize panel headers
* 44d008d HUE-6077 [frontend] Linked editor list to parametrized home
* 682d6bf HUE-1176 [jb] Remove SLA from API before using embedded page
* 825f18d HUE-6132 [metadata] Adding test for query missing partition filters
* 8ad6743 HUE-6077 [frontend] Remove double scroll from the editor help modal
* 874b4c2 HUE-6077 [frontend] Support for clearing app subscribers and hook up on Editor
* f558fa6 HUE-6077 [frontend] Support for pause/resume of huePubSub topics
* c82aba5 HUE-1176 [jb] Do not split running and finished jobs in two categories
* d118965 HUE-6176 [frontend] Add tooltip to main button
* f281e8f HUE-6176 [frontend] Integrate dynamic configuration in the assist panels
* 2d4a9ae HUE-6176 [frontend] Integrate dynamic configuration into the left menu
* ac121fa HUE-6176 [frontend] Integrate dynamic configuration into the top create menu
* 9f7f872 HUE-6176 [frontend] Integrate dynamic config to the mainQuickCreateAction
* e36ea30 HUE-6176 [frontend] Harmonize app permissions in UI
* ced539b HUE-6077 [menu] Harmonize left menu hierarchy
* 63a72cb HUE-6077 [menu] Rename Oozie to Scheduler
* 0f39ebc HUE-6177 [frontend] Fix the hover colour on the main menu items
* c3f80d7 HUE-6177 [frontend] Add icon for job designer
* d5f40de HUE-6173 [assist] Fix js error when clicking in empty editor
* 86b3efb HUE-6162 [core] Humanize the missing load balancer message
* a7eacee HUE-6077 [frontend] Disable feedback on the query button
* 1278706 HUE-6077 [frontend] Ship an embedded woff/woff2 of Roboto and Roboto Mono
* f71958d HUE-6161 [doc2] Move document conversion upgrade into a migration
* 5201b17 HUE-6162 [core] Display a warning and offer to switch to the LB port if Hue is on a non-LB port
* 4402182 HUE-6173 [assist] Make sure the right assistant is loaded when opening saved editors
* ece5f1d HUE-6173 [assist] Improve statement locating in the right assistant panel
* 5039b12 HUE-6174 [editor] Show the correct editor type in the new button tooltip
* f543302 HUE-6077 [frontend] Use the correct border colour for the assist panel resize
* e4f8812 HUE-6172 [editor] Prevent loading the editor twice in Hue 4
* b26c61c HUE-6171 [editor] Add disposal logic to the SQL worker
* cbe8928 HUE-6132 [metadata] Add tests against false positive cross joins
* fae9a87 HUE-6132 [metadata] Improving query upload result message
* c82bf13 HUE-6077 [frontend] Removed unused LESS styles from the workflow editor
* 4dc8584 HUE-6077 [frontend] Reduce size of the start/end node in the workflow editor
* f5ecc83 HUE-6077 [frontend] Fixed curved arrows display on Oozie workflow editor
* 3ab1701 HUE-6077 [frontend] Avoid leaking of .active from the document browser
* 09bb7f7 HUE-6077 [frontend] Avoid re-initializing the mini jobbrowser at every job count check
* 59bae76 HUE-6077 [frontend] Avoid JB2 to pick up all the hashchanges events
* d2abcaa HUE-6077 [frontend] Lighten up vertical scrollbars
* 0c5a613 HUE-6077 [frontend] Dropped MathJax
* f42bbf0 HUE-4631 [home] Prevent TransactionManagementError resulting from history document conversion failure
* 745e52b HUE-6132 [metadata] Update the test and add a series of risk queries
* 94fd706 HUE-6132 [editor] Add list of risks in assistant
* 7da6ab8 HUE-6077 [frontend] Remove border from card class
* 0acaa31 HUE-6077 [frontend] Switch to cui color for elephant trunk
* b2ae258 HUE-6168 [search] Unify the search header with the rest of the apps
* 56b164f HUE-6167 [frontend] Add svg icons for dashboard and editor
* 2608023 HUE-6077 [frontend] Centralize the app icons
* 79205bb HUE-6166 [frontend] Add svg icon for R
* 7613db2 HUE-6165 [frontend] Add sag icon for py
* dda4efb HUE-6164 [frontend] Add svg icon for spark
* c59e112 HUE-6163 [frontend] Add svg icon for pig
* 155f0ed HUE-6077 [frontend] Create button improvements
* 639f8c4 HUE-6077 [frontend] Fixed styles for search dashboards
* 8914f06 HUE-1176 [jb] Tentative refresh button on jobs list
* 76c8d3a HUE-1176 [jb] Adding bulk actions to jobs and workflows
* a910751 HUE-1176 [jb] Skeleton for browsing of Job tasks or Coordinator instances
* ce0805b HUE-1176 [jb] Use action button templates for all YARN jobs
* d785631 HUE-1176 [jb] Protect against YARN jobs in accepted state
* 93e8ab4 HUE-1176 [jb] Protect YARN fields against missing values
* 9307c94 HUE-1176 [jb] Move workflow specific code to a method
* c6d06ff HUE-1176 [jb] Workflows action button logic
* a6cbb4a HUE-1176 [jb] Workflow action button logic
* 4ac2b89 HUE-6077 [frontend] Add top border to Hue 4
* dfd6cb8 HUE-6077 [frontend] Assign app to the JB2 intervals so they can be paused and resumed
* d2e2212 HUE-6077 [frontend] Fix jHueScrollUp positioning for the file viewer
* 4eaccb5 HUE-6077 [frontend] Fixed search field on jHueSelector
* 115454f HUE-6077 [frontend] Centralized analytics functionalities
* 2141b48 HUE-6077 [frontend] Override the font weight of form labels
* 70040a1 HUE-6077 [frontend] Expand the filechooser tree to the full width of the panel
* de596ae HUE-6077 [frontend] The horizontal scrollbar should have an inferior z-index than the modal backdrop
* 4456c29 HUE-6077 [frontend] Restyled Hue 3 top menu hovers
* 3c6e7fa HUE-6077 [frontend] Unified Hue dark blue to cui-blue-700
* 888603d HUE-6077 [frontend] Override nav-tabs border width to 2px
* 6ba9985 HUE-6077 [frontend] Converted colors of breadcrumbs to CUI
* 73750ea HUE-6077 [frontend] Update bootstrap editable to 1.4.6 and fix a positioning bug
* db984b1 HUE-6132 [metastore] Hide advanced metadata tabs
* 3f99032 HUE-1176 [jb] Basic checkboxing on list of jobs
* 98ace2b HUE-1176 [jb] Automatic refresh of job
* 014ca1a HUE-1176 [jb] Automatic refresh of jobs
* 6f577a3 HUE-6157 [core] Fix various live cluster tests
* 0e6e64a HUE-6077 [frontend] Switch to the common left-nav design
* 21777ae HUE-6077 [frontend] Hide IE reveal password icon
* 11f22ce HUE-6077 [frontend] The filechooser actions should be on the same line in Hue 4
* bf8116e HUE-6077 [frontend] Added breadcrumbs to LESS
* d193d5a HUE-6132 [optimizer] Provide the SQL type to the recommendation call
* c9952aa HUE-5939 [metastore] Add decimal to the list of available types
* 82e1d8c HUE-6077 [frontend] Simplify querystring forwarding
* feb203f HUE-6077 [frontend] Grouped assist hover styles in the LESS file
* 2b65bd3 HUE-6117 [fb] Support shift + click to select multi rows
* 0fb3cbf HUE-5817 [editor] Bigger/easier result grid horizontal scrolling
* 2e23216 HUE-6077 [frontend] Fixed select files button on FB
* 725ed34 HUE-6077 [frontend] Fixed filechooser sizes and updated the upload button style
* 4998676 HUE-6077 [frontend] Fix top menu for Hue 3
* 6704939 HUE-6077 [frontend] Give context to the current hovered items on the assist
* d95bd53 HUE-6158 [autocomplete] Don’t remove characters to the right on insert
* b73d186 HUE-6148 [frontend] Revert new svg icon for Hue documents
* 21ef6a6 HUE-6153 [hbase] Log debug instead of exception messages for fallback handling
* ed85f60 HUE-6143 [editor] Reset query history page to 1 when searching
* 2036f37 HUE-6151 [editor] Add jasmine tests for SqlAutocompleter3
* 463026b HUE-6077 [frontend] Add drop shadow to login form
* 93c014f HUE-6077 [frontend] Improve compress files modal dialog
* 403ded9 HUE-6077 [frontend] The modal buttons shouldn't be at least 120px wide
* 6bb4b55 HUE-6077 [frontend] Harmonize extract icons on FB
* c2ff40d HUE-6077 [frontend] Support the old /notebook routes too
* 9cba3d0 HUE-6077 [frontend] Fixed size of breadcrumbs on Metastore
* 0692e9b HUE-6155 [core] Remove table extender header throttling for Firefox
* 181f585 HUE-6154 [core] Ace paste event shouldn't reset the cursor position
* 4b8abb8 HUE-6099 [fb] Prompt for a filename when compressing as batch job
* e0546af HUE-6144 [oozie] Add generic XSL template to workflow graph parser
* 4221dea HUE-6151 [editor] Catch all js exceptions in the autocompleter
* 1afcee8 HUE-6148 [frontend] Add svg icon for Hue documents
* 13cc91b HUE-3727 [editor] Use the new hueLink binding to open query directory
* 76cc838 HUE-6143 [editor] Add pagination to the query history
* 9df3fbc HUE-6132 [navopt] Catch early NavOpt API 500
* 0b67ce8 HUE-6132 [metadata] Better handling of topTables error
* ca54d94 HUE-6077 [frontend] Fixes query builder on Hue 3 and port the styles to common
* e7b5f65 HUE-6147 [assist] Add initial right-click context menu for Hue documents
* b948465 HUE-6147 [assist] Add initial right-click context menu for HDFS
* c892c60 HUE-6146 [assist] Update the assist source when switching editor in Hue 4
* 565aa0b HUE-6077 [frontend] Moved open.link fallback to common_header
* 589853b HUE-6077 [frontend] Avoid opening history and job panels at the same time
* 335842b HUE-6077 [frontend] Simplified top bar and removed dropdown carets
* 5c876f8 HUE-6077 [frontend] Unify colors throughout
* a60111d HUE-6145 [assist] Prevent js error when assist search hasn’t been initialised in time
* 069b405 HUE-6077 [frontend] Ported hue-scrollbar to common LESS
* 621721f HUE-6077 [frontend] Ported hue-spinner to common LESS
* 6228ca2 HUE-6077 [frontend] Unify page.route and open.link
* 49fadfc HUE-6077 [frontend] Adding missing var
* 01aa9a1 HUE-6142 [editor] Update the editor type when loading the document
* be2220a HUE-6077 [frontend] Remove lonely li end tag from left nav
* 992ca65 HUE-6141 [editor] Fix asterisk expansion popover
* 3c35e86 HUE-6077 [frontend] Fix missing location hover styles for ace
* ea65dd4 HUE-6140 [oozie] Use svg icons for Oozie
* 3475be0 HUE-6077 [frontend] Fix dropdown hover colors
* 878ffcd HUE-6077 [frontend] Added login modal support to Hue 4
* 6b6ebff HUE-6077 [frontend] Added blurred class to common LESS
* fdc304e HUE-5767 [core] Started restyling the login page for Hue 4
* b03e957 HUE-6077 [frontend] Fix the old jobbrowser spinner
* 6b3733b HUE-6077 [frontend] The jHueNotify alert should be hidden by default
* b638272 HUE-6077 [frontend] Added /logout route
* 691df45 HUE-6077 [frontend] Unified jHueNotify alerts with CUI
* eb4b9e9 HUE-1176 [jb] Add initial Oozie pagination
* 7131d20 HUE-6132 [metadata] Convert the queries to the proper upload format
* c2a589a HUE-6077 [core] Update the top menu link to Job Browser
* 15ee37a HUE-6080 [metadata] Add size limit to the optimization API
* cac4893  HUE-1176 [jb] Reload a page with a coordinator id and keep the breadcrumbs
* cb8a94a HUE-1176 [jb] Reload a page with a workflow id and keep the breadcrumbs
* 9836e28 HUE-1176 [jb] Reload a page with a job id and keep the breadcrumbs
* 14bd730 HUE-6132 [assistant] Send empty risks when there is none
* 58fb828 HUE-6077 [about] Use correct default URL in Hue 4
* bc2f41f HUE-5788 [editor] Remove all github code
* fe5739e HUE-6132 [assistant] Support a list of hints
* 0b5342f HUE-6138 [editor] Add page route for specific job links
* 257ece2 HUE-6138 [frontend] Clean-up page mapping
* cbf8cf9 HUE-6138 [frontend] Reintroduce lodash
* 23ced04 HUE-6138 [frontend] Add ko binding for hue links
* 8706f10 HUE-6138 [editor] Fix job link overlay positioning
* a8697f6 HUE-6077 [frontend] Enlarged default modals
* 1b495cf HUE-6077 [oozie] Scroll the right element on action drop
* ec8d970 HUE-6077 [frontend] Added cross versions CSS for the Hue tour
* 7c8aa52 HUE-6077 [frontend] Added cross versions CSS for demi-modal and selectize
* 4824a3a HUE-6136 [core] Retain original last_modified date after setting is_trashed for converted docs
* 1e82215 HUE-6131 [hive] Select partition values based on the actual datatypes of the partition column
* 36727eb HUE-6101 [fb] Archives with space in the name cannot be extracted using batch job
* d1a5778 HUE-6098 [fb] Right click on a zip shows compress instead of extract
* 7845e23 HUE-6077 [frontend] Moved app-icon CSS to cross versions
* e384d4f HUE-6077 [frontend] Fixed some Oozie workflow URLs
* 50f60e5 HUE-6077 [frontend] Fixed home linking
* 9b5e606  HUE-5853 [oozie] Revert embeddability of lists
* b612ab6 HUE-6077 [frontend] Removed references to spinner-big.gif
* 064142c HUE-6077 [frontend] Added newer BS2 to fix the btn-inverse color
* 9fc8033 HUE-5853 [oozie] Port list of bundles to Hue 4
* 5bf3964 HUE-5853 [oozie] Port list of coordinators to Hue 4
* 6eba212 HUE-5853 [oozie] Port list of workflows to Hue 4
* 60ea4b2 HUE-6132 [assistant] Extract table names from metastore table format
* 0eb3cb6 HUE-6077 [oozie] App menu link should support Hue 4
* dbaa5c3 HUE-6077 [core] Remove titles that conflicts with the compose menu
* c05a9e7 HUE-6132 [editor] Add default DB to the uploaded queries and DDL
* 2d7c3d5 HUE-6132 [editor] Update table upload input format
* b122697 HUE-6132 [metadata] Suppress console error log when metadata entity can not be found
* 66ddb43 HUE-5831 [assist] Improve styling of document icons in the assist panel
* 7f88750 HUE-5831 [assist] Use the svg document icons in the assist
* e74a916 HUE-6135 [assist] Fix editor document URLs
* 7432092 HUE-6077 [frontend] Remove conflicting inline styles from the assist
* 1f472fa HUE-6133 [home] Stricter check for activeEntry existence
* 23363b7 HUE-6133 [home] Avoid search blinking
* 7281557 HUE-6133 [home] Typing on the search box crashes IE 11
* f7b26e9 HUE-6091 [core] Avoid infinite looping and pick better default landing page depending on perms
* 630c50b  HUE-1176 [jb] Integrate text, status and time filtering to Oozie Workflows
* 78fd692 HUE-1176 [jb] Introduce pagination to the YARN job listing
* aa90cb8 HUE-1176 [jb] Link YARN job states filtering logic
* 04251cf HUE-1176 [jb] Integrated time filtering to YARN jobs
* 9e63236 HUE-1176 [jb] Split the list of jobs into running and finished
* 2e0a82e HUE-6134 [assist] Use the MetastoreTable for tables in the assistant
* 47b5387 HUE-6134 [metastore] Extract global var for metastore options
* f6c17f3 HUE-6134 [assist] Extract the metastore models
* d646957 HUE-6077 [frontend] Added hueach to both versions
* 2ace84a HUE-6091 [core] Added /metastore route
* cc8198f HUE-5439 [assist] Add database comment and a link to the Metastore DB page in popover
* b285502 HUE-6111 [editor] Potential display of many zeros in snippet execution time
* bf599a1 HUE-6077 [frontend] Port scroll to anchors to a LESS component
* ff7c2f9 HUE-6128 [hive] Default custom authtentication to PLAIN instead of failing
* add4270 HUE-6091 [core] Fix routing for Search
* 000974a HUE-6091 [core] Fix routing for Metastore
* 107ab8e HUE-6077 [frontend] Open gethue.com links in a new window
* 21e0dbf HUE-6077 [frontend] Serve the http 500 file in case of a load app error
* beaf07e HUE-6077 [frontend] Card toolbars shouldn't be transparent
* ab099cf HUE-6077 [frontend] Oozie workflow add action shouldn't be wrongly placed on drop
* 82f8678 HUE-6077 [frontend] Changed dragged widget title background
* 7807790 HUE-6077 [frontend] Fixed LESS main component for the common dashboard and added it to Oozie
* 979a98d HUE-6115 [core] Fix document paths for names with unicode characters
* bcf3b57 HUE-6091 [core] Offer a potential back history link on the 404
* 704f6f6 HUE-1176 [jb] Filter yarn jobs on text
* 49b22a4 HUE-1176 [jb] Adding fetching of the proper log names
* e21271c HUE-1176 [jb] Clicking on section should always switch to it
* ad493ea HUE-1176 [jb] Adding template of job time filter
* 4f84768 HUE-1176 [jb] Adding SLAs page
* f212be9 HUE-1176 [jb] Do not lose breadcrumb hierarchy when navigating jobs
* 4d0e50b HUE-1176 [jb] Move Oozie workflow specific code out of core logic
* 2cb6a67 HUE-6122 [core] Aggregate task history snippets into a single task that gets updated
* a4db095 HUE-6077 [frontend] Drop hue3.css from Hue 4 pages
* a608d0f HUE-6077 [frontend] Fix input alignment issue in tab headers
* 8aa9433 HUE-6077 [frontend] Switch to latest CUI bootstrap
* 066b9f5 HUE-6124 [search] Fix dashboard header
* 06ca9db HUE-6125 [sqoop] Moved styles to LESS
* fcbd271 HUE-6125 [sqoop] Port to Hue 4
* ec519be HUE-6118 [core] Re-introduce the top banner in Hue 4
* 92dfeaa HUE-6123 [notebook] Add refresh button to file statement type and remove snippet read only mode
* f95e3aa HUE-6077 [hbase] Declare mako template as utf8 to avoid string extraction issues
* 1ad414c HUE-6091 [core] 404 error page
* b9c0292 HUE-6091 [editor] Do not use the cached history when loading an editor of different type
* 2e798cb HUE-6091 [core] Improved loading logic of apps
* c43de81 HUE-6091 [core] Force to editor if a route is not found
* 1b3ec56 HUE-6077 [frontend] Improve background color for multi-level dropdowns
* f37d8c4 HUE-6077 [frontend] Fix double icon issue in assist search results
* 0da9284 HUE-6121 [frontend] Fix issue with compose menu icon colors and switch to svg icons for Hive and Impala
* a9ff13b HUE-6120 [metadata] Fix the assist search result context popover in the Impala editor
* b592fe1 HUE-6113 [frontend] Prevent dashboard css from leaking
* 51b4d04 HUE-2142 [editor] Test with still an invalid batch snippet type value
* e97a0e7 HUE-6112 [notebook] Add save to File button for 'file' statement type
* 389e6b5 HUE-6091 [fb] Remove missed embeddable variable
* 1aa7802 HUE-6116 [editor] Avoid js error when fetch result size in not available
* f73af7f HUE-6091 [editor] Change the url to /hue/editor in Hue 4
* e9bb183 HUE-2142 [editor] Convert saving result to an index in Hue 4
* bbc0fc9 HUE-2142 [editor] Convert exporting result to a dashboard in Hue 4
* d035c29 HUE-2142 [editor] Convert saving result to a table in Hue 4
* 0847c6d  HUE-4627 [editor] More intuitive names for query export to a directory task
* 87a9172 HUE-4627 [editor] Do not insert history statements in the regular history
* 32f95bb HUE-4627 [core] Add counter of finished and running tasks
* 208e741 HUE-2142 [editor] Convert saving result to a file in Hue 4
* bb0b167 HUE-3727 [home] Add new query links action on homepage in old Hue
* 6b4b3ed HUE-6091 [core] Fixed a JS error on waitForObservable
* 47d81b1 HUE-6077 [frontend] Prevent notebook css from leaking
* 2d0d5af HUE-6077 [frontend] Style the compose menu
* d633ee6 HUE-6091 [core] Improved waitForObservable
* 6dd9a57 HUE-6091 [core] Ported all the open.link routes to page
* be75f27 HUE-6091 [core] Simplified filebrowser routing
* f4c05bc HUE-6091 [core] Swapped currentApp links to page routing
* bea6f5a HUE-6091 [core] Improved management of URLs for editor
* c685a12 HUE-6091 [core] Removed is_embeddable from the base urls
* 20ba1c1 HUE-6109 [core] Remove the restriction on Document2 invalid chars
* 7896436 HUE-6104 [aws] Check if boto configuration section exists before adding it
* 3a5b324 HUE-6103 [fb] Log filesystem initialization exceptions
* fb82bc6 HUE-6105 [assist] Bacward compatible with Hue 3
* ef73341 HUE-6108 [editor] Fix sqlite execution and syntax highlighting
* 7e5ec09 HUE-6091 [core] Fixed webpack entry point naming
* c8584c7 HUE-6105 [assist] Hide app not enabled from appearing in the panel
* d68f3fc HUE-6091 [core] Re-organized webpack
* 56220f5 HUE-6091 [core] Changed dashboards to follow the is_embeddable format
* 8d772b2 HUE-6091 [core] Default open to editor
* f9a0413 HUE-6091 [core] Changed home to follow the is_embeddable format
* 435f5fb HUE-6091 [core] Changed notebook to follow the is_embeddable format
* 8502b9a HUE-6091 [core] Changed editor to follow the is_embeddable format
* 0adb6a1 HUE-6091 [core] Ported useradmin to page.js
* 06f2a9b HUE-6091 [core] Catch all URLs on /hue
* d550037 HUE-6091 [core] Added Page.js
* b4bfc3f HUE-6077 [frontend] Improved styling of top bar in the new pages
* 0b1cce2 HUE-6107 [assist] Fix JS error when filtering pig functions
* ec27784 HUE-6077 [frontend] Hue3.css clean-up round one
* 8c13051 HUE-3996 [libdbms] Offer downloading query results
* af94536 HUE-5853 [oozie] Move the new workflow node dropping to async
* 6b47340 HUE-6087 [core] Pause intervals when the app is in background in Hue 4
* 466ac05 HUE-6087 [core] Initial port of per-app intervals to the new format
* 02364b5 HUE-6092 [autocomplete] Fix JS error when parsing joined subquery locations
* a1cef1b HUE-6092 [autocomplete] Extract parser js logic to a separate file
* d8d4ab9 HUE-6077 [frontend] Drop the border from .container-fluid
* 6d7236c HUE-6089 [core] Simplify user menu in Hue 4
* bf538c2 HUE-3727 [home] Create new editor document from home directory in responsive
* 68821b0 HUE-6087 [core] Add pauseable and resumeable intervals to the window object
* 21b1e62 HUE-6089 [core] Adding missing endif on hue.mako
* 578ecd9 HUE-2142 [editor] Default value of export_result API should be in json
* f2fb4e2 HUE-6080 [core] Adding rsa package as it is a dependency for metadata
* f50f65d HUE-6080 [metadata] Avoid none casting in navopt lib versioner
* 6148e7d [HUE-6090] Hue to do a keep alive on idle sessions to HiveServer2
* e8582d3 HUE-4866 [fb] Add button to open sql files in editor
* 7dcbeec HUE-6077 [frontend] Moved login modal styles to LESS
* 5d513cb HUE-6080 [core] Adding asn1crypto lib as required in metadata lib
* b950d2b HUE-6080 [metadata] upgrade the API with sizing parameters
* ccdd711 HUE-2142 [editor] Convert saving to a directory of result data to the task framework
* 3dfa59d HUE-6088 [core] Scroll top top and to left should be aligned with the app panel
* 9fea7e7 HUE-6077 [frontend] Improve hbase styling
* 09dd20d HUE-6077 [frontend] Improve the styling of the tab search for query history and saved queries
* fee0534 HUE-6077 [frontend] Improve sample table styling in the context popover
* bea69f6 HUE-6077 [frontend] Improve SQL context popover styling
* e7a8b94 HUE-6086 [assist] Fix js error when opening a complex type
* a4c8a18 HUE-5965 [security] Moved CSS to LESS
* e2e3b9f HUE-5853 [oozie] Moved all CSS files to LESS
* abe92ae HUE-5964 [core] Port add/sync ldap user to Hue 4
* 63f4d8a HUE-6066 [metastore] Add EXTERNAL_TABLE to the list of DEFAULT_TABLE_TYPES in hive_server2_lib so Hue will show external tables in database meta info. (#496)
* 705e620 HUE-6077 [frontend] Switch context popover from nav-pills to nav-tabs
* 409ae4e HUE-6077 [frontend] Fix editor metadata explanation
* 4b75e9f HUE-6077 [editor] Improve hover effect on the result tab actions
* acb0832 HUE-6082 [core] Unified the common menubar of the admin wizard
* 2a574bd HUE-6082 [core] Initial port of the dump config page
* 76644e7 HUE-6082 [core] Initial port of the logs page
* 3b0615c HUE-6082 [core] Initial port of the admin wizard page
* 3b594c0 HUE-6082 [core] Initial port of the help page
* 8c7926c HUE-5814 [assist] Fix issue with infinite scrolling in the hdfs assist panel
* 8ce8557 HUE-6077 [frontend] Switch from nav pills to nav tabs in the right assist
* a909f83 PR-504 [autocomplete] Fixed a bug where autocompletion would break on subqueries (#504)
* 3921884 HUE-4866 [editor] Operation to open up an external query file
* 0f12352 HUE-5988 [metastore] Fix old test issue uncovered in API revamp
* 801c667 HUE-6077 [frontend] Fix Oozie button styling
* a676a23 HUE-6077 [frontend] Improve importer styling
* 03db1dc HUE-6077 [oozie] Improved draggable bar resize loop
* 99a3b6a HUE-6077 [editor] Fixed results grid
* 95c8440 HUE-6077 [frontend] Improved sortable look for old Hue
* 89bb87b HUE-6077 [frontend] Made BS2 span3, span9 and margin variables globally available
* 838c0e0 HUE-6077 [frontend] Improved spacing in the app-specific navbar
* e666eae HUE-6077 [frontend] Fix the snippet progress bar
* 7f41ae8 HUE-5965 [sentry] First port to Hue 4
* e3c8bb7 HUE-6077 [frontend] Changed 'responsive' to simply 'hue'
* fcaf6e6 HUE-6077 [frontend] Unify the border colors for the editor
* 9ac23d6 HUE-6077 [frontend] Fix styling of assist search input
* 8fa4336 HUE-6077 [frontend] Add missing endif
* dc5cc27 HUE-6077 [frontend] Added missing BS2 img files
* c26cc91 HUE-6077 [frontend] Replace x by &times in modal to avoid codec error
* e3dd0c4 HUE-5988 [importer] Generate proper LOAD data for partioned table created from a file
* b80bebf HUE-2533 [useradmin] Only show information updated when it is true
* a4e9c45 HUE-3294 [responsive] Add app permissions to the menu
* 741badd HUE-3294 [responsive] Refactor compose menu logic
* 98d5b01 HUE-6077 [frontend] Link home to home page in responsive
* 6049961 HUE-5988 [importer] Add partition values logic into the indexer front end
* 81355d9 HUE-6079 [metastore] Make load data work with responsive
* 0db78fa HUE-6077 [core] Fixes tooltip attachment container
* e7fdc1d HUE-6077 [frontend] Pass the whole onePageViewModel to the job-browser-panel component
* 1156f2a HUE-6068 [assist] Protect against missing metastore app
* a767e49 HUE-6077 [frontend] Make hamburger menu closable in responsive
* dd20674 HUE-6077 [frontend] Fix white background on pill navigation and move the page contents up
* 2668c92 HUE-6077 [frontend] Fix top nav caret color in old pages
* ea8b20f HUE-6077 [frontend] Added Vimeo as valid security exception
* 3edc271 HUE-6077 [frontend] Removed local Roboto fonts
* 05d5267 HUE-6077 [frontend] Fix all modal headers
* 88f4f24 HUE-6077 [frontend] Added Google fonts as valid security exception
* f095191 HUE-6077 [frontend] Fix top navbar button alignment
* 720b043 HUE-6077 [frontend] Removed 'theme' from makefile
* 9b25bed HUE-6077 [frontend] Fix styling of search container in assist and top bar
* cb08009 HUE-6077 [frontend] Use the CUI top navbar in responsive
* 02342e9 HUE-6077 [frontend] Delete the bootplus source
* ff0d15c HUE-6077 [frontend] Remove the .nav hover effects for Hue 3
* 1dfeef8 HUE-6077 [frontend] Fix app header positioning
* a787966 HUE-6077 [frontend] Remove the left and right margin and border from container-fluid
* 0f6061f HUE-6077 [frontend] Remove the use of .navbar-inverse
* b013199 HUE-6077 [frontend] Replace bootplus with CUI bootstrap
* ee143d2 HUE-6072 [core] Restyle document import result dialog
* a3a5e03 HUE-6073 [hbase] Port to Hue4
* 39fb73e HUE-6075 [oozie] Remove email body while displaying external graphs in dashboard
* d42f5f5 HUE-1176 [jb2] Fix typo when getting graph element id
* 0b5c89a HUE-5684 [oozie] Prevent page break when hiding workflow graph
* 14d9b01 HUE-5911 [assist] Sqlite database is erroring in the table assist
* 51fbceb HUE-4963 [metastore] Convert table data browsing to responsive
* 893c776 HUE-4963 [metastore] Convert partition browsing to responsive
* 7bbe234 HUE-4963 [metastore] Convert partition browsing to the new editor
* 1a1b1ea HUE-4963 [metastore] Convert partition file browsing to the new editor
* 867ab6c HUE-6071 [frontend] Only show the right assist when we have contents
* f8079c7 HUE-6070 [frontend] Extract job browser panel to a separate ko component
* 0633d02 HUE-6069 [frontend] Extract history panel to a separate ko component
* 2f44bab HUE-6068 [assist] Let the contents of the right-click context menu be dependent on the active app
* ff30876 HUE-5963 [oozie] Prevent drag and drop of action into action arguments
* 6127dfd HUE-5964 [useradmin] Made edit user page embeddable
* da74068 HUE-6067 [responsive] The loaded job browser should respond to all the hashchange events
* b0df4a0 HUE-5967 [search] Create dashboard should work in responsive
* 5db4f04 HUE-5967 [search] The indexes link in the dashboards page should open in responsive
* 191475c HUE-5967 [search] The dashboards link in the indexes page should open in responsive
* fcc602e HUE-5972 [core] Avoid showing delayed tooltips if the element is not visible anymore
* ce6996f HUE-6065 [assist] Improve the insert at cursor functionality
* 457b5ba HUE-6064 [assist] Enable right-click context menu for databases in the assist panel
* a0bc285 HUE-6062 [frontend] Make sure the left and right panels don’t take up space when closed
* b270ecc HUE-6060 [metastore] Open table location link in file browser in responsive
* 6cfc320 HUE-6060 [importer] Add collection of usage hints
* 0a5c4ac HUE-6060 [editor] Support dropping databases in responsive
* b2c7c01 HUE-6060 [importer] Ko-ify prefilling properly in order to work with responsive
* ee33f7c HUE-6060 [editor] Unify isManaged and isTask job types together
* 923cdbb HUE-6060 [editor] Enable clearing the task history
* da9f9e6 HUE-6063 [core] Removed a wrong rel value for tooltips
* 8c0361e HUE-6063 [core] Second round of IE spinners removal
* 8dbad66 HUE-6063 [core] Added alt property to img tags
* 4f77124 HUE-6063 [core] Remove IE specific spinners
* c524f3e HUE-6063 [core] Script tags without a src attribute shouldn't have charset specified
* db881aa HUE-6061 [editor] Sorting the results table by id should re-render the first column on the fly
* 86c94b7 [HUE-6055] Need http_client for navigator
* 372a0ad HUE-6012 [metastore] Support dropping a single table in responsive
* beb6163 HUE-6012 [metastore] Disable the assist refresh in batch submission mode
* fea2477  HUE-6012 [metastore] Support dropping tables in responsive
* 0b265ad HUE-6012 [metastore] Add links to open the importer in responsive
* 9854358 HUE-3228 [dashboard] Automatically enabled in Hue 4 or when search is enabled
* 254283f HUE-6012 [metadata] Skeleton to port dropping tables into single page app
* d97c6ad HUE-5929 [metastore] Show sample API errors in the panel instead of as a page notification
* f4bb8bc HUE-6059 [assist] Show authentication error messages in the assist search
* 4883078 HUE-6057 [autocomplete] Allow more whitespace around ? completions
* 2674499 HUE-6056 [assist] Hide the assist search results when clicking show in assist
* 913c263 HUE-5964 [useradmin] Moved CSS to LESS
* 47f13c9 HUE-5329 [metastore] In columns section, we show "view more" when there are no extra rows
* a9fb8d7 HUE-6058 [responsive] Fix left menu dropzone click behavior and existing upload handler
* 02e4e91 HUE-5964 [useradmin] Ported list of configurations
* 7f2d684 HUE-5964 [useradmin] Converted ID elements to classes
* 5df1548 HUE-5964 [useradmin] Ported list of permissions and generalize filter element
* 409d1da HUE-5964 [useradmin] Specify parent node on the groups page jQuery
* 7fc409d HUE-5964 [useradmin] Removed unused json call and fixed tests
* 7878feb HUE-5964 [useradmin] Simplified port of the user list
* 0c60283 HUE-5964 [useradmin] Ported list of groups
* 39c9c1d HUE-3164 [fb] bzip2 files cannot be viewed properly in HUE file browser
* 1cfdb23 HUE-6044 [metadata] Escape special chars of DisMax Solr parser
* ae7b1e3 HUE-6053 [home] Ignore history docs and fix links in trash confirmation popup
* ab2b912 HUE-6052 [oozie] Fix workflow dashboard status button filtering
* 34e5918 HUE-6048 [doc] Refresh of the translations
* 552951f HUE-6050 [autocomplete] Fix issue where autocompletion might fail because of parser exception
* f68285f HUE-6050 [autocomplete] Add support for aggregate functions as column names in the autocompleter
* 5bf0015 HUE-6049 [importer] Renders deeply nested selects on fields in IE11
* bbdf78c HUE-6049 [importer] Improved rendering for manually created tables
* 1cda77a HUE-6049 [importer] Fix bottom margin for the field list
* 222ec18 HUE-6049 [metastore] Check for additional nullpointers on HueDataTable
* 50c7def HUE-6049 [editor] Enable search icon just on grid display
* d795a94 HUE-6049 [metastore] Check for null table on fnAddData
* 6110db9 HUE-6042 [editor] Handle missing tables, columns and functions in the sql context popover
* bc90cce HUE-6047 [desktop] Skip test_is_trashed_migration test to prevent failing oozie tests
* 1a897d4 Revert "HUE-5919 [oozie] Oozie related tests are missing documents and failing"
* 3e4b576 HUE-6046 [metadata] Trim the default key used in the privilege checker
* 76273c0 HUE-6045 [pig] Progress bar doesn't turn green on completion
* fe1f946 HUE-3228 [dashboard] Only enable Solr in the default config
* cd21c82 HUE-6039 [metadata] Check for combinations of cluster names
* 967de2b HUE-6043 [metadata] Explicit handling of authentication error
* d048e9e HUE-6034 [search] Dashboard with HTML results shouldn't throw a JS error
* acd98fd HUE-5724 [assist] Keep the formatting when copying the view sql definition
* 0b71729 HUE-5724 [assist] Apply SQL formatting to the view sql in the context popover
* 276564f HUE-5724 [assist] Drop the option to insert view sql at cursor and only have click to copy
* 226bb5e HUE-6041 [importer] Custom field separator should be propagated to all instances of it
* 83b9cfc HUE-6040 [autocomplete] Rename value meta type to sample
* d06bbaf HUE-6034 [search] Having an undefined field shouldn't show a JS error
* 7cddaa2 Revert "HUE-5408 [oozie] Fix indentation"
* 3e447cb HUE-6038 [metadata] List partition names on search instead of nothing
* 002d049 HUE-6033 [importer] Do not require the indexer permission
* 458bdeb HUE-5848 [core] Auto logout window can trigger an infinite loop on /notebook/api/notebook/close
* 5cb3e59 HUE-6037 [metadata] Allow views in the get_table call
* ac2a990 HUE-6036 [assist] Fix js error when tagging databases
* 33c25ea HUE-6035 [editor] Fix editor js error from huePubSub
* 6966d2f HUE-5964 [useradmin] Fix list users test assertion
* 48cbe0b HUE-6031 [core] Searching for a non-existing column on the sql popover shouldn't give a JS exception
* 91220b8 HUE-6032 [responsive] The mini and the regular jobbrowsers should co-exist
* 05ffb20 HUE-6030 [autocomplete] Prevent double group by suggestions
* 2efeec1 HUE-5724 [assist] Format the view SQL in the context popover and add copy and insert actions
* fcfe98c HUE-6027 [core] The Autocompleter shouldn't overflow on the header
* 430b5d3 HUE-6029 [core] NiceScroll should hide just when the mouse leaves the scrolling element
* defc5d8 HUE-6028 [importer] The page shouldn't fail if the sample has less than 2 rows
* eb85c56 HUE-5870 [importer] Added bottom margin to display all the columns for a small table
* 585fad9 HUE-5870 [importer] Handle collection size changes in the foreachVisible binding
* e625383 HUE-5870 [importer] Improve performances for tables with a lot of columns
* c494856 HUE-5964 [useradmin] Added open.link handler for responsive
* 58fe6dd HUE-5964 [useradmin] Added user list loading spinner
* a0e39e7 HUE-5964 [responsive] Added user list
* f3a8d7c HUE-5964 [core] Added jHueRowSelector KO binding
* 45d2c0c HUE-5964 [useradmin] KOify user list page
* ae00d1d HUE-6025 [metadata] Support fetching view object in search_entity
* 26592f8 HUE-6020 [oozie] Missing Hive query document when new layout is not activated
* 7a9ac80 HUE-6021 [metastore] Allow nicer formatting of metadata description
* 28e0d9d HUE-6024 [assist] Avoid js error on assist search with no entities in the response
* b76eb3b HUE-6023 [metastore] Fix js error when loading tags in the metastore
* 7af277c HUE-6022 [assist] Send the correct type for views when fetching the nav entity
* 90874ba HUE-6010 [assist] Make sure the search autocomplete spinner gets removed on search
* 6320861 HUE-6013 [metastore] Remove top right view location action
* bccaa33 HUE-5937 [metastore] Do not show old editor warning when dropping tables
* 1e8cb3b HUE-6011 [editor] Hint on potentially missing jar registration when using Json table serde
* ee64271 HUE-5724 [assist] Show the view SQL in the context popover
* d8aefdc HUE-6008 [assist] Replace partials including facets when autocompleting non-facets in search
* c9437a1 HUE-5982 [assist] Show all available DB sources in the assist panel
* 819e371 HUE-6016 [core] Set login_not_required to jasmine tests
* 19ad421 HUE-6015 [editor] Bind dropzone to a common element across editor and notebook
* 90ddba7 HUE-6007 [metadata] Parent filtering can conflict with facet type as they are ORed together
* 9a6c310 HUE-5989 [metastore] Better retry UX when submitting table fails the first time
* 1a5635e HUE-6004 [assist] Fix database context popover in the assist search results
* 91c7a0f HUE-6003 [assist] Append instead of replace when selecting a value from search autocomplete
* d984e5a HUE-6002 [assist] Don’t show the tag editor for other sources than Hive and Impala
* 318446b HUE-6001 [assist] Slow down the entry indication on search result click
* cd16d65 HUE-6000 [assist] Show search autocomplete errors in full
* 4c25764 HUE-5959 [backend] Allow 0 as a setting for conn_max_age
* 10fe643 HUE-3947 [editor] Offer to manually run queries in editor when sample data timeouts
* 7ad8d11 [HUE-5959] Enable Persistent connections using CONN_MAX_AGE
* 411ce1c HUE-5999 [metadata] Use the proper path of the entity in the search autocomplete or selection
* df1ca23 HUE-5898 [importer] Create DB should check for already existing DB
* 2076646 HUE-5997 [metastore] Kudu table should submission not be enabled without a PK
* f157f65 HUE-5996 [metastore] Create table manually should not be available with default.
* ae3b92d HUE-5992 [metastore] Kudu manual table creation with comment fails
* 543850a HUE-5993 [metastore Manual CSV create table error is unclear
* 25ed265 HUE-5994 [spark] Kerberos support config
* da54c14 HUE-5987 [metadata] Proper error handling of Entity not found
* 1facf07 HUE-5986 [editor] Only serialize expiration message if it is actually some text
* 9030d59 HUE-5984 [search] Escaping corrupts link-meta for building external links in grid dashboard
* 8cd67e6 HUE-5934 [assist] Don’t show tags for databases when metadata isn’t configured
* 224c751 HUE-5971 [importer] Improve 'create a new' label UX
* 1cc2f63 HUE-5974 [importer] Bulk editing field names shouldn't show the old field names
* 4869f41 HUE-5973 [metastore] The ‘query this table’ icon is misleading
* 485f020 HUE-5981 [meatstore] Fix issue with samples tab not showing in the context popover
* d33a9b9 HUE-5980 [metastore] Fix js error when opening tables from the assist
* 6618fd5 HUE-5979 [metastore] Fix js error when listing tags fails with status: -1 and no message
* f8491ff HUE-5978 [autocomplete] Fix issue with moving cursor to ‘?’ after completion
* a3bf64f HUE-5976 [assist] The sort dropdown aligns to the left
* 0f6f5bd HUE-5975 [assist] The sort icon is off screen by default
* c51196a HUE-5977 [assist] The table counter and filter icon should be hidden while we are refreshing
* 5045739 HUE-5509 [notebook] Properly handle unicode characters in log output in jdbc connector
* 04d0537 HUE-5962 [hiveserver2] Update HiveServerClient user object when opening session
* 5bb4b05 HUE-4743 [editor] Queries don't need to have ms in the time counter(do not show more than 2 digits for precision)
* 611781e HUE-5961 [doc] Update testing.rst to include the Jasmine URL
* 35876d4 HUE-5949 [responsive] Wire in dropzone on the left menu
* 0bd166f HUE-5952 [assist] Show a message in the search autocomplete on error if a reason is given
* 588f17d HUE-5940 [autocomplete] Replace partial word to the right when inserting
* 9b0d337 HUE-5956 [metastore] Create DB shouldn't use default all the times
* 50f951a HUE-5956 [core] Hide hive chooser on click when skipTables is specified
* 14cdb3e HUE-5960 [importer] The fixed top bar should adapt to responsive
* f249505 HUE-5945 [core] Fix for anonymous user protection
* 24851bf HUE-5958 [pig] Fix unicode errors when handling exceptions
* d2fcfb3 HUE-5945 [core] Protect against anonymous user having his home dir pulled
* 4b3e7d7 HUE-5957 [metadata] Clicking on table name should add DB prefix too in autocomplete
* 5b53dc7 HUE-5898 [importer] Create a new database does not warn when the DB already exists
* 21ed22a HUE-5955 [metadata] Returns cause of error in interactive search
* 40ab26a HUE-5954 [indexer] Make the index list dependent on having Search enabled only
* 7d30f29 HUE-7 [importer] Adding Avro as list of output format
* 5cb6c69 HUE-5859 [jdbc] Fix librdbms problem when CLASSPATH variable not defined in environment
* c671475 HUE-5950 [importer] Wire in dropzone on the page for a quick file upload
* 9694c4d HUE-5952 [assist] Add error handling to assist search
* 372c133 HUE-5951 [assist] Close the assist search spinner on error
* eebb5a5 HUE-5948 [metadata] Remove debug code from tags editor
* 58ce6b3 HUE-5947 [fb] Bind dropzone to the right DOM element and not to body
* 4b719fd HUE-5945 [core] Add a Knockout Dropzone binding to support file upload anywhere
* 52b250a HUE-5946 [editor] Drag and drop of a sql file from the desktop doesn't work anymore
* c93bd3c HUE-5948 [metadata] Add error handling to the tag editor
* 6d7f188 HUE-5944 [metastore] Rename tagging to tags
* c34b389 HUE-5941 [home] Enable keyboard shortcut to select all the documents like on a desktop
* a775ae5 HUE-5942 [sqoop] The detail of a job shouldn't show submissions if there aren't any
* c1b79cd HUE-5938 [metadata] Retrieve ids of sources of a certain cluster
* 9578371 HUE-5937 [editor] Hint user using the old SQL editor that they should switch to the new one
* 677175b HUE-5936 [metastore] Currently selected DB should be used instead of default all the time
* 743bf14 HUE-5936 [metastore] Offer manual table creation from metastore database page too
* 75ca82a HUE-5819 [editor] Check status frequency should slow down with time
* 06463b5 HUE-5931 [impala] Simpler error message when the query expired
* e99f911 HUE-5935 [importer] Opening the importer without a prefill throws a JS error
* 4e0462a HUE-5891 [importer] Create database placeholder should be more accurate
* e57cfe4 HUE-5892 [importer] Fix all the existing table error message links
* 91cc5e1 HUE-5932 [metadata] Add client-side validation to the tag editor
* ef0acd1 HUE-5931 [editor] Move results graying out to pubSub and fixed first column margin
* 6a0f7e5 [HUE-5930] [Backend] Make cx_Oracle compilation optional in cx_Oracle 5.2.1
* 1fc2cf7 [HUE-5930] [Backend] Upgrade cx_Oracle python library to 5.2.1
* 700f62a [HUE-5816] Changing default setting as allowed_hosts=['*']
* 6c1cfd2 HUE-5170 [spark] Use spark schema 0.2 only when the actions contains a file
* b1b5e37 HUE-5608 [editor] Support displaying column of partitioned tables that have Sentry column permissions
* c02168a HUE-5928 [metastore] Table page of partitioned table crashes even if user has some column level access
* 965263c HUE-5925 [sentry] Privilege checker call Sentry API2 without a required parameter
* 3cfb5fd HUE-5261 [editor] Move rowcount polling fetching to frontend
* 175945e HUE-5608 [editor] Display table column list even if user only has some column level access
* 7d3fffc HUE-5926 [sentry] hiveChooser seems flaky and does not autocomplete columns
* 47e5760 HUE-5859 [notebook] dbproxy_extra_classpath property in hue.ini does not seem respected
* edf3291 HUE-5924 [responsive] Default fallback for loading Metastore
* 93e51b1 HUE-5888 [fb] Right click and unselect file in FB keeps the context menu open
* 628a926 HUE-5923 [assist] Show a spinner when search autocomplete is loading
* d6c2689 HUE-5094 [metastore] Fix initial loading of tables and databases
* 7e2bb5f HUE-5921 [assist] Don’t show the assist search autocomplete after pressing return
* 7f31c16 HUE-5918 [assist] Fix issue with initial autocompletion of assist search
* f267fd3 HUE-5880 [core] File chooser should have a refresh icon
* 97b71c3 HUE-5881 [importer] Guessing the format of a file crashes IE11
* 2eb0c91 HUE-5897 [importer] Choose file shouldn't show the select this folder option
* ef84434 HUE-5897 [importer] ko.bindingHandlers.filechooser option to hide 'Select this folder'
* 65d1cc5 HUE-5894 [importer] Page scroll should update the hive chooser dropdown position
* d969463 HUE-5893 [core] Hide hive chooser autocomplete when empty
* d365712 HUE-5890 [importer] Steps shouldn't have a pointer cursor if it's not possible to select them
* 09f6b0b HUE-5920 [editor] Hivechooser for the export should use the new ApiHelper
* c4a4d4e HUE-5919 [oozie] Oozie related tests are missing documents and failing
* 1e1ae0e HUE-5917 [metadata] Properly mock metadata API and activate the tests
* 0da05f7 HUE-5917 [metadata] Move pullin user privileges at initialization
* e704615 HUE-5917 [metadata] Add Django caching of security permissions
* 8c3a27d HUE-5916 [metadata] Securely filter database, views and columns
* eded0f9 HUE-5889 [importer] Create a new database has a pointer cursor but nothing happens on click
* a5a30fe HUE-5915 [importer] Friendler error message when trying to create table from a directory
* 6d2b905 HUE-5901 [importer] Disable submission if one of the column has an empty name
* 7800926 HUE-5796 [assist] Cancel previous assist search calls when typing fast
* 2e743ee HUE-5207 [assist] Fix the go to assist action
* 94748e3 HUE-5906 [autocomplete] Fix issues with the autocomplete dropdown in IE 11
* a0499da HUE-5905 [assist] Fix issue where search autocomplete dropdown is shown on page refresh in IE 11
* 72fc994 HUE-5904 [assist] Use nicescroll in the search autocomplete dropdown
* 443cbba HUE-5908 [oozie] The Impala action should list the impala queries
* 9b611f6 HUE-5846 [metadata] Another update properties from service to server
* f1ee5d6 HUE-5895 [metadata] Show useful part of error when DB creation fails because of permissions
* cb2562d HUE-5876 [importer] Remove View collection and print error messages if any
* 5249fb6 HUE-5907 [oozie] Loading a workflow misplaces the draggable icons toolbar
* cdf13f7 HUE-5883 [editor] Remove weird spaces from a query on paste
* a1c5eb3 HUE-5885 [editor] Remove double scrollbar on the editor help
* e539a6a HUE-5875 [metastore] Drop database modal message is misplaced
* 7708a33 HUE-4664 [fb] "Delete forever" message should be more specific
* 4cbce3e HUE-5879 [core] SVG path tags shouldn’t be self closing
* c714483 HUE-5878 [beeswax] Fix malformed tags on IE11
* 055f50d HUE-5887 [oozie] Persist documents and actions choice on workflow editor
* e72ca86 HUE-5846 [metadata] Update ini with the updated property names
* cbc34ed HUE-5864 [oozie] Polishing on non secure cluster
* 6b93aec HUE-5865 [assist] Move sorting inside the filter box
* 8ccc4c9 HUE-5864 [oozie] Add an Impala document action
* 10fa3ea HUE-5863 [oozie] Add an Impala action
* aaccda7 HUE-3281 [responsive] Integrate back the polling of jobs
* 9728f73 HUE-5873 [editor] The download in progress modal doesn't close automatically on IE11
* 44e60d7 HUE=5872 [core] Fix apiHelper error handling on IE11
* 340398f HUE-5871 [jasmine] Fix hue.utils test on IE11
* 7a80cf1 HUE-5804 [assist] Truncate long entry names in the assist search
* c651219 HUE-5853 [oozie] Make documents and actions switchable in the workflow editor
* 12bcf96 HUE-5803 [assist] Drop the assist search result count
* d170d96 HUE-5801 [assist] Fix search autocompletion of partial facets when selecting something other than a facet
* 977ac6a HUE-5801 [assist] Move search styles to less
* 0551ba4 HUE-5801 [assist] Extract search to a separate module
* 02762ee HUE-5244 [assist] Close the context popover on esc
* 9b084c4 HUE-5832 [autocomplete] Add initial jasmine tests for SqlAutocompleter3
* 29cf9ff HUE-5868 [jb] Make the new job browser embeddable without a nav bar
* 7c27db0 HUE-5793 [editor] Trunc() UDF documentation should list all the available formatting formats
* 62ee8e2 HUE-5862 [fb] Remove smiley and message on empty files
* bdf9c53 HUE-5866 [oozie] Remove smiley from SLA
* 0082a43 HUE-5867 [rdbms] Remove smiley
* d6bf045 HUE-5131 [impala] Better error message when all the query cache was used
* bbc3323 HUE-5858 [assist] Supporting file open from git browser in assist
* 8455d69 HUE-5408 [oozie] Fix indentation
* d103587 HUE-5686 [editor] Fix the Pig autocompletion of paths
* c9bab7a HUE-5807 [autocomplete] Limit the popular entries to 10 except for under the popular tab
* b8037d8 HUE-5839 [autocomplete] Improve autocompletion around CTEs
* 8751517  HUE-5857 [editor] Integrate automatic query compatibility check from any platform
* c7f1eb9 HUE-5857 [editor] Offer a list of source platforms for compatibility
* 35797a2 HUE-5857 [editor] Prevent blinking of the risk alert
* 3cb7b07 HUE-5857 [editor] Only spin on manual compatibility check
* 3767a7d HUE-5855 [search] The field list and results autoresize should work with multiple instances of them on the page
* 143327f HUE-3955 [editor] Saving a query should update its description in the saved query list
* 9b2b3ce HUE-5756 [doc2] Set is_tashed for all children recursively when trashed or restored
* 80e9ea5 HUE-5851 [fb] Support the new S3 regions
* ee244e1 HUE-5829 [responsive] Oozie action buttons shoudln't navigate away
* 2dbc37a HUE-5853 [core] Better JS and CSS loading detection on responsive
* b82d52f HUE-5853 [oozie] Fix margins for the workflow title and z-index of draggable widgets
* 6a6c74a HUE-5853 [oozie] Avoid infinite loop on toolbar resize
* 53713dd HUE-5846 [metadata] Update test to read from the lineage property file
* 83da6f7 HUE-5764 [editor] Remove manual links to hints
* 2c94b0d HUE-5850 [sentry] Prevent creating roles with empty names
* c3029e7 HUE-5852 [editor] Fixed status with empty query
* ef7dc44 HUE-5852 [editor] Show spinner on query compatibility checks
* 6d098a8 HUE-5847 [autocomplete] Hide the autocomplete dropdown when there are no matches after typing
* a65ab7d HUE-3228 [search] Rename the wrong imports
* 3331de5 HUE-5846 [metadata] Update conf file to read the latest properties
* 941b3da HUE-5840 [autocomplete] Cache any response, empty or not, in the apiHelper
* 83ba741 HUE-5845 [assist] Fix issue with primary key showing for all columns
* 31233f0 HUE-5815 [editor] Improve tooltip for column expansion
* 651799a HUE-5797 [editor] Don’t show the assist search autocomplete on focus
* ee1d720 HUE-3228 [dashboard] Adding localization messages
* 3b91c1a HUE-5844 [oozie] Document workspace path parameterization
* 2f5fecd HUE-5792 [search] Change Hivechooser to use ApiHelper and the correct engine
* ab68c76 HUE-5764 [metadata] Further style the complexity and syntax validation
* 5f82f6b HUE-5841 [metadata] Sample popup not showing up when listing certain databases in Search
* 77cdef5 HUE-3228 [dashboard] Unify the hue.ini properties
* 2666255 HUE-5792 [search] A new dashboard should start from an empty slate
* 34ea0a0 HUE-3228 [dashboard] Refactor the dashboard configuration
* 8410459 HUE-3228 [dashboard] Move out of Dashboard the Solr specific code
* 718844e HUE-5833 [impala] Remove the old dashboards
* 2a0801e HUE-5833 [dashboard] Unify dashboard logic into its own library
* 995079a HUE-3228 [dashboard] Iteration on displaying empty buckets for the timeline
* 9655803 HUE-3228 [dashboard] Better handling of number range facet
* 1f28feb HUE-5792 [search] Dynamic creation of a new dashboard
* 1aa4912 HUE-5792 [search] Ko-ify creating a new dashboard
* 50c9b2b HUE-5565 [core] Avoid trademark font overlap on login page
* 1c42cc0 HUE-5742 [core] Set default schema to public
* ba6dc44 HUE-5756 [Doc2] Add test for migrations on is_trashed field
* ec01e0e HUE-5756 [Doc2] Update test_document_trash
* 9028c15 HUE-5756 Add is_trashed to Doc2 model
* 1360ac5 HUE-5837 [search] Delete index confirmation should be in line with all the other delete modals
* 89d84d4 HUE-5838 [core] Fix mobile imports
* 42230a0 HUE-4852 [metastore] List the tables that are going to be deleted in the popup
* 948c9a2 HUE-5835 [importer] Creating a new database should not error
* 3c53cb4 HUE-5788 [core] Set default file type icon for non directory files.
* 6de0cdc HUE-5824 [editor] Add keyboard shortcut for formatting and make the editor help searchable
* dab3a34 HUE-5686 [editor] Add Ace keyword and function completion for Pig
* a0346df HUE-5834 [metastore] Show metastore links directly in responsive
* 3062c48 HUE-5828 [autocomplete] Fix errors related to autocompletion of subqueries
* f3a613b HUE-5826 [editor] Make sure there are no gaps between statement locations reported by the parser
* c2dd0c0 HUE-4741 [editor] Menu can be hidden by Saved query name/description textarea
* 9cf9433 HUE-5565 [responsive] Avoid leaking of Oozie workflow css
* 66a4fce HUE-5822 [oozie] Select all should select just the visible workflows/coordinators/bundles
* 96159f1 HUE-5827 [home] Remove step by step tutorials
* 79df208 HUE-5571 [core] Move the window.zoom event to the shared footer code
* 15564ed HUE-5826 [assist] Show assistant info for only the focused statement
* 19e696c HUE-5826 [editor] Adjust parser to also report statement locations
* 44a13e0 HUE-5812 [frontend] Add disposal logic to the niceScroll binding
* 9f7f7f7 HUE-5812 [frontend] Improve sluggish scroll after multiple editors opened in responsive
* 2dfd19f HUE-5812 [frontend] Fix leaking job count requests
* d7b87b4 HUE-5825 [editor] Downloading a query result might have double extensions
* 337438f HUE-5716 [impala] Fix failing test test_impala_flags:test_impala_flags
* c91b7bf HUE-5788 [core] Add github api to list files in assist
* 054e324 HUE-5823 [editor] Cancel running doc search requests when the query has changed
* 10ab8d0 HUE-5821 [core] Add the first round of compressed CSS files
* 28eaaa2 HUE-5821 [core] Compress the generated CSS files and add a banner to them
* 16430ed HUE-5810 [assist] Open assist documents directly in responsive
* 5928467 HUE-5809 [assist] Use the correct database name for creating tables and add creation of databases
* 4652b29 HUE-5811 [assist] Align assist doc icon to the right
* 2adc68f HUE-5808 [assist] Don’t fetch popular columns when metadata is disabled
* 180747a HUE-7 [metastore] Turn on the new create wizard
* 8ae8163 HUE-5806 [editor] Impala is casesensitive when listing tables of a database
* c2c8574 HUE-5802 [editor] Integrated scheduler submission should not require a database id
* 086f311 HUE-4473 [oozie] Extend to generic parameters too
* 6e397c9 HUE-5795 [notebook] Add the type of snippet in the execute call
* f0326c9 HUE-3228 [dashboard] Display fetched record by get_document
* 337fce4 HUE-3228 [dashboard] Get record by ID if one column is a PK
* 53da454 HUE-5789 [search] Add 'link' as an optional link to an external document
* b24d87f HUE-3228 [dashboard] Skeleton of Time filter override and range
* e3dcfc4 HUE-3228 [dashboard] Add proper casting from bigtint to timestamp
* 48d0d1a HUE-3228 [dashboard] Proper last N time filtering with isBigIntDate
* 9e51842 HUE-3228 [dashboard] Allow bigint to be a date field for the timeline in SQL
* 68ac8f1 HUE-3228 [dashboard] Add initial engine list to Browse action
* 0b106be HUE-3228 [dashboard] Turn off auto refresh when in fixed time filter
* 0d2f50a HUE-3228 [dashboard] Support auto refresh
* 63f4f58 HUE-3228 [dashboard] Add first rolling or fix global date filtering
* 21e4268 HUE-4473 [oozie] Bulk add parameters and arguments
* 5906498 HUE-5779 [importer] Fields in id list not updated when Creating Kudu table
* 480608a HUE-5716 Add impalad_flags to impala conf and set dynamic default values
* 5ab626d HUE-5716 [impala] Use get_webserver_certificate_file from impalad_flags to check if ssl is enabled
* 33f4928 HUE-5776 [editor] Drag & drop a SQL shows up when dragging the table info icon in assist
* 9d3b5b8 HUE-5785 [editor] Selecting a pivot resets the Y axis the first time
* 15330be HUE-5746 [editor] Extension missing when download result from a saved query
* 0ce3ff1 HUE-5790 [metadata] Remove deleted deletetedTime facets
* db3eb0b HUE-5787 [indexer] Newly created collection do not have an ID field
* 82a428a HUE-7 [metastore] Checkbox target should only be on the checkbox
* bf047c3 HUE-5777 [editor] current_timestamp is missing () in autocomplete
* 23da3a4 HUE-5765 [editor] Show correct error line number when statement is not on top
* dcdcfde HUE-2214 [fb] Add replication factor in menu and do not show compress action in S3
* a539ad0 HUE-2214 [fb] Display and set replication
* c1ef809 PR 478 [TK] Improve of Japanese for Hue 3.12 (#478)
* 26ed072 HUE-5721 [jb] Support text filtering on Workflows tab
* 215be38 HUE-5783 [core] Bump version to 3.12
* 5030c88 HUE-4969 [core] Rename ini properties for sasl buffer to be standard
* 37aa76d HUE-5406 [editor] Do not restart at zero when adding or removing a multi query
* 10410e0 HUE-5406 [editor] Support editing last statement of a multi query without restarting
* 04ceb5d HUE-5775 [editor] Show grid sort icon just on hover
* 59e7bc0 HUE-5774 [editor] Fix JS null pointer on data.jobs
* 83ee79c HUE-5773 [assist] On certain cases a JS error is shown on the db panel
* 66db8a0 HUE-5772 [search] Show Auto refresh option only when it's a rolling time window
* 4786d36 HUE-5770 [search] Extended property to numeric and changed binding to textInput
* ba1a30e HUE-5770 [search] Auto refresh option is only triggered once
* beda97b HUE-1176 [jb2] Remove graph arrows on tab hide
* 29493d5 HUE-5771 [useradmin] Checkbox click binding should work also after a pagination event
* 841f7ef HUE-5769 [oozie] Remove mandatory inclusion of Kill row in the workflow dashobard graph
* d6e3148 HUE-5406 [editor] Stay on statement of a multiquery when editing and re-executing
* 37f064d HUE-4715 [editor] Formatter does not put LIMIT on a new line
* 67c1444 HUE-5764 [metadata] Style syntax check and complexity results
* 6c8d1bd HUE-3228 [dashboard] Select date range on timeline widget
* 9c30829 HUE-3228 [dashboard] Add timeline with timestamp type
* 49879cf HUE-3281 [core] Unify some test config flags
* 6d3df45 HUE-3228 [dashboard] Support number range facet display
* 6c6f985 HUE-3228 [dashboard] Support number range filtering in fq
* 599e5df HUE-3228 [dashboard] Support number instance in fq
* 05bd007 HUE-3228 [dashboard] Compatibility with Hive group by syntax
* b8844b5 HUE-3228 [dashboard] Support range number in facets skeleton
* 2291d6b HUE-5766 [openid] Declare module to avoid import error
* 9d243e7 HUE-5757 [importer] Add CSV Table format
* 043d790 HUE-5759 [metastore] Jump to column on table page does not update the horizontall scroll bar position
* bde6bbf HUE-7 [importer] Improved vertical alignment of some checkboxes
* a097496 HUE-7 [importer] Better vertical alignment of selectize components and restyle of Index fields
* ef8f2d4 HUE-7 [importer] Restyle of bottom bar and correctly enabled the wizard circle step 2 click
* e2730b7 HUE-7 [importer] Restyle manual field list
* 41eaecf HUE-7 [importer] Harmonize vertical spacing of step 2 properties
* 29d7d1a HUE-7 [importer] Change label extra to extras
* cecd7a5 HUE-7 [importer] Add CSSStyleSheet.prototype.addRule polyfill
* acded61 HUE-5762 [security] Reverting X-Content-Type-Options default option from False to True
* 34388da HUE-5717 [backend] Some operating system incorrectly detect javascript mime-type as text/x-js instead of application/javascript
* b98e1dc HUE-5670 [doc2] Prevent exception when doc2 object is not linked to doc1
* e907c94 HUE-5504 [oozie] JDBC URL specified in Hive2 action should override credential properties
* d717ee8 HUE-5742 [core] Allow user to provide schema name for database via ini
* 2692490 HUE-5758 [oozie] Fix parsing nodes from XML definition
* 3eba751 HUE-5712 [metadata] Add extra table and column stats to the upload
* cc5f8c9 HUE-5755 [jb2] Remove debug div
* de2d2f2 HUE-5743 [core] Add D3 v4 to Hue
* 5ef998c HUE-5751 [core] Make HiveChooser binding and plugin updatable
* d05191f HUE-5752 [sentry] Make Hivechooser use the new apiHelper calls
* 9acaf04 HUE-5753 [metastore] Make Hivechooser use the new apiHelper calls
* a6a24d3 HUE-5754 [core] Create a generic Ace editor binding
* 450d9a1 HUE-5750 [importer] Better UX when creating a table manually
* cdb1300 HUE-5749 [metadata] Add audit call when editing metadata
* 0e46b95 HUE-5748 [libdbms] Add _TYPE suffix to JDBC connector
* 6fff643 HUE-5747 [librdms] Add column types to MySQL queries
* 3eb397b HUE-5660 [home] Restore documents from Trash to /home
* 06e237f HUE-5736 [core] Queue all the nav opt calls in the ApiHelper
* 5bede4f HUE-5736 [core] Extract the ApiHelper queue logic to a separate object
* 351a091 HUE-3228 [dashboard] Save new status of batch/task jobs if it changed
* acb9a24 HUE-3228 [dashboard] Do not historify the dashboard queries
* 11276c7 HUE-7 [metastore] Avoid js error when DB is not loaded directly
* c9591bb HUE-7 [importer] Support creating a kudu table from a text file
* a3c82ae HUE-5734 [editor] Fix issue where the context popover highlighter marks invalid locations after a syntax error is introduced
* 3d36b08 HUE-5733 [editor] Fix js errors related to typed keywords
* b6a5a9f HUE-5732 [editor] Fix js error in the sql context highlighter
* abd6970 HUE-5731 [editor] Enable the new autocomplete dropdown by default
* 7c59698 HUE-5730 [editor] Fix issue where the autocomplete dropdown doesn’t show after page zoom
* 9d0f0e2 HUE-5729 [editor] Move the * to the top in the autocomplete suggestions
* 21eeeee HUE-5728 [editor] Update Ace highlighting for Impala DESCRIBE statements
* e3ae944 HUE-5728 [editor] Update the autocompleter for Impala DESCRIBE statements
* a874fa1 HUE-5659 [home] Ignore history dependencies when importing document from different cluster
* f315761 HUE-5722 [core] Avoid query redaction when string is None
* 52055f6 HUE-5506 [fb] Add Compress action to right click menu
* bc7eb25 HUE-5727 [assist] Add column popularity to the assist
* 9a9b266 HUE-5699 [assist] Show a star next to popular tables in the assist
* e120983 HUE-5715 [responsive] Keep left and right panel widths in total storage
* b82c2d6 HUE-5725 [core] Add the generated cui-bundle
* 33e78a3 HUE-5725 [core] Add webpack
* 1b9db6a HUE-5708 [editor] Add highlighting of UPDATE for Impala
* 07a7ed4 HUE-5712 [metadata] Upload DDL and available stats of active tables and their columns
* 4bef9a6 HUE-5712 [metadata] Upload table and column stats in the new json format
* d0bcf72 HUE-5726 [core] Sandbox the old D3 with nvd3 to support the new d3 v4
* 2378602 HUE-5563 [responsive] Add the context panel and display sessions for the editor
* ca18e91 HUE-5694 [editor] Improve re-open timings for autocompletion of ‘? FROM db.table’
* 8299802 HUE-5710 [core] Move the notebook styles to less
* fedb015 HUE-5402 [oozie] Allow user to enter local time for SLA nominal time
* faaa0d5 HUE-3228 [dashboard] Migrate get document call to common API
* 882f50b  HUE-3228 [dashboard] Support adding old timeline in current mode
* 996a1be HUE-5720 [indexer] Pickup the Solr default solr.ulog.tlogDfsReplication replication when creating examples
* ea6b52a HUE-3228 [dashboard] Add saveResultsModalVisible to allow to show the export data modal
* b243944 HUE-3228 [dashboard] Only return the selected fields in a grid widget
* e8555ec HUE-5216 [filebrowser] Support folder upload from desktop
* 358d939 HUE-1176 [jb2] Use the new HiveChooser ApiHelper integration
* 4c75fba HUE-5718 [core] HiveChooser should re-use the assist caches for autocomplete
* 6f70584 HUE-5716 [impala] Add impalad_flag file format reader
* b619c52 HUE-5719  [notebook] Recheck status when received status "waiting" (#475)
* bbe6acb HUE-5713 [assist] Fix default sort order of columns
* 98d3d1f HUE-1176 [jb] Shortened breadcrumbs
* b062f30 HUE-1176 [jb] Remove curved arrows at any job fetch
* e971f62 HUE-1176 [jb] The graph actions shouldn't link away from JB2
* ac7bbaf HUE-1176 [jb] Update action statuses on the imported workflow graph
* 204d0c4 HUE-3228 [dashboard] Support other SQL that have a sync API
* 4cdbd4b HUE-7 [importer] Avoid moving of elements next to the HiveChoosers
* 7065edb HUE-5714 [hive] Close SQL canary query "Select "Hello World""
* 6e61c7b HUE-5712 [metadata] Update API that now contains stat upload
* a97fb84 HUE-5712 [metadata] Filter popular tables by database name
* 1d10831 HUE-5408 [oozie] Support old docs while saving shared workflow
* bdd6514 HUE-5685 [editor] Indicate primary keys with an icon in assist and the autocomplete dropdown
* 8010552 HUE-5709 [core] Move the metastore styles to less
* 50eb1c4 HUE-5708 [editor] Add ace highlighting rules for kudu create table statements
* cc725a9 HUE-1176 [jb2] Support more than a graph at a time
* bb66828 HUE-5645 [notebook] Fix issue where the save results dialog disappears on mouse movements
* e837ecf HUE-1176 [jb2] Plugged in Workflow graph
* b1295f0 HUE-7 [importer] Restyle table existing alert
* 413854e HUE-7 [importer] Show invalid field as red
* 5afe4d6 HUE-7 [importer] Enable all File formats when running indexer tests
* 50f1ffc HUE-7 [importer] Accept to read gzip files in source
* b8e0fea HUE-7 [importer] Disable loading data in S3 tables
* 7df0908  HUE-7 [importer] Automatically sync output field delimiter value based on input
* 2111e29 HUE-7 [importer] Automatically sync output header default value based on input header value
* e5c688a HUE-7 [importer] Combine extra properties in a show toggle on/off
* 46e2faa HUE-7 [importer] Adding a warning and preventing submission if table already exists
* 410d65f HUE-7 [importer] Properly detect TSV input files
* 6793ea6 HUE-7 [importer] Prevent creating table with names already existing
* c240915 HUE-3228 [dashboard] Add automatic close statement of previous queries
* 769d3a3  HUE-3228 [dashboard] Add manual WHERE filters into the queries
* a5b282d HUE-3228 [dashboard] Offer to cancel all non finished queries
* 16d2c91 HUE-3228 [dashboard] Unify progress button to wait for all facets to finish
* 9ef6c58 HUE-3228 [dashboard] Split APIs in sync and async
* e3f0fe3 HUE-3228 [dashboard] Integrate with Notebook result download
* a5c675a HUE-3228 [dashboard] Only apply aggregates that are after the last dimension
* 393fd0c HUE-3228 [dashboard] Support dimension 2 facet graph
* ec31016 HUE-3228 [dashboard] Support aggregates in facets
* 0bfd644 HUE-3228 [dashboard] First version of total number of rows
* 9f8cd89 HUE-3228 [dashboard] Fix logic of distinct count function
* bdb29d0 HUE-3228 [dashboard] Async submission and status fetching
* 0f0121e HUE-3228 [dashboard] Migrate to Notebook API
* 0159b68 HUE-5707 [editor] Extract autocomplete styles into less
* 1fa3978 HUE-5696 [editor] Fix issue where the popularity star is sometimes missing in the autocomplete dropdown
* 8092d22 HUE-5698 [editor] Lower the autocomplete weights for TABLESAMPLE and LATERAL VIEW
* e595303 HUE-1176 [editor] Fix highlighter error
* 875685e HUE-5450 [responsive] Extract embedded assist styles to separate less file
* e110f76 HUE-5450 [responsive] Extract common less values and attributes
* 19ae535 HUE-5450 [responsive] Extract less for assist panel
* 07ea737 HUE-1176 [jb2] Fixed hide/show assist panel
* c961087 HUE-1176 [jb2] Harmonized breadcrumbs
* 09cc26f HUE-1176 [jb2] Restyled top bar
* 455453a HUE-1176 [jb2] XML display binding and clean up of load links
* 6a7a5bd HUE-7 [importer] Fixed resize elements
* 4426bf3 HUE-7 [importer] Set visual clue that hiveChooser is loading tables
* 8270bcc HUE-7 [importer] Set source.show when a table name is present
* fa7e730 HUE-7 [importer] Prefill assist database into hivechooser
* 3567552 HUE-7 [importer] Made table field longer
* 53e232f HUE-7 [importer] Fix wizard header line overflow
* 1bce27a HUE-7 [importer] Show edit fields bulk icon on hover
* 1309391 HUE-7 [importer] Changed headers style and make the page a bit more compact vertically
* 61ec98c HUE-7 [importer] Put separators on one line
* 251c94e HUE-5706 [core] Put back responsive.css for development purposes
* f4c10e7 HUE-5706 [core] Updated package.json
* e5bef4c HUE-5706 [core] Use grunt watch to listen to less file changes and recompile automatically.
* 9191522 HUE-5706 [core] Use Grunt to build less.
* eca7da9 HUE-5661 [fb] Filechooser seems to truncate the file list
* e20d91a HUE-5703 [security] Upgrade totalStorage and pass along a secure cookie fallback in apiHelper
* 90096b2 HUE-5702 [security] Mark as secure the hueLandingPage cookie if on https
* ea465af HUE-5701 [security] Remove last references to $.cookie and migrate to $.totalStorage from FB
* 0cc2b4d HUE-5689 [importer] Top progress section is small in FF
* ef8812c HUE-7 [importer] Tweak the UX and add flags to enable the new version
* c00bd21 HUE-5700 [security] Reverting X-Content-Type-Options default option from True to False
* 7330730 HUE-1176 [jb2] Add check app status and progress to the API
* df2d781 HUE-5691 [metadata] Parameterize search fetch call limits
* c530a1d HUE-5690 [metadata] Need to filter data to the current Hue cluster only
* 74150a8 HUE-5688 [metadata] Filter out facet values when Sentry filtering is on
* f2470d1 HUE-5115 [dashboard] Add support for function widget
* 18f996a HUE-5646 [editor] Include table and column comments in the autocomplete filter
* 4025eb2 HUE-5687 [editor] Show HDFS details in the autocomplete dropdown
* eb81662 HUE-5683 [editor] Show details for popular aggregate functions in the autocomplete dropdown
* eb16823 HUE-5682 [editor] Show details about joins and join conditions in the autocomplete dropdown
* e4ac796 HUE-5681 [editor] Add details for popular order by, group by and filter to the autocomplete dropdown
* 8734f5f HUE-5693 [editor] Set autocompletion argument types for avg() to numeric for Impala
* f779c81 HUE-7 [importer] Varchar numbers do not need to casted to numbers
* b77b410 HUE-5115 [dashboard] Support merging multiple filter facets from different widgets
* a0a5264 HUE-5115 [dashboard] Add field facet selection filtering
* 19ddf1c HUE-1176 [jb] Add new coordinator page
* 2d7fe5c HUE-5680 [editor] Update autocomplete dropdown categories based on active filter
* 763b1d3 HUE-5674 [editor] Detach the autocomplete dropdown details panel
* 6d0b750 HUE-5673 [editor] Don’t wrap long suggestions in the autocomplete dropdown
* c04dc70 HUE-5676 [editor] Improve filtered prefixed suggestion weights
* 3cc72e5 HUE-5633 [editor] Show column details in the autocomplete dropdown
* 24016d2 HUE-5506 [fb] Update arguments in Notebook() initialization
* 6afaf31 HUE-5506 [fb] Update message in submission notification popup
* 7f87b14 HUE-5506 [fb] Add unit test and small nits
* 0306081 HUE-5506 [fb] Add script to compress hdfs files
* c5adc71 HUE-5506 [fb] Add compress utils API that submits batch job
* e068c40 HUE-5506 [fb] Add backend API
* cd6cbdb HUE-5506 [fb] Frontend to submit file compression as batch job
* 64aa36f HUE-5684 [oozie] Hide workflow graph when node count > 30
* 83da46a HUE-5684 Prevent duplicate nodes in the workflow graph layout
* 36f1637 HUE-3228 [search] Fix import that was not properly renamed
* 44cbbb3 HUE-5679 [impala] Do not truncate the last part of rows in result downloads
* 98e182e HUE-5677 [metadata] More robust and friendly check upload status
* d946b54 HUE-5632 [editor] Add popularity to table details in the autocomplete dropdown
* a870101 HUE-5647 [editor] Improved colors in the autocomplete dropdown
* 78b6d9c HUE-5675 [editor] Fix js error from complex type completion in the new autocomplete dropdown
* 3707710 HUE-5672 [editor] Fix issue with empty autocomplete dropdown
* 01c3947 HUE-5661 [editor] Add skeleton of SQL assistant
* 9ea372b HUE-1176 [jb2] Do not trigger a fetch job when none are selected on page load
* e0ce7a9 HUE-3228 [dashboard] On/off flag to allow SQL in dashboards
* 16ad708 HUE-4908 [editor] Support sample popup on Kudu tables
* f9c711d HUE-4908 [editor] Add metadata flag when the table supports updates
* f94965f HUE-3228 [dashboard] Create a new dashboard by selecting a table or and index
* 3376fca HUE-4908 [metastore] Add primiary key icons to the Kudu columns
* f44a9d8 HUE-4908 [importer] Update Kudu table creation format
* 535bf62 HUE-3228 [search] Adding more than one aggregation dimension to facets
* 6ede306 HUE-3228 [search] Add column metadata to grid facet
* 5c4eb5d HUE-3228 [search] Support listing tables
* 14ab43c HUE-3228 [search] Add SQL facet logic
* 9d4b9f9 HUE-3228 [search] Skeleton of common API
* 308ca58 HUE-1176 [jb] Reload job via URL hash
* 585bc48 HUE-1176 [jb] Add workflow action page
* 0c54762 HUE-1176 [jb] Add tasks to the workflow page
* f793c23 HUE-1176 [jb] Add configuration to the workflow page
* a3e423d HUE-1176 [jb] Add XML definition to the workflow page
* b767dde HUE-1176 [jb] Add basic job operation API to workflows
* c663b7b HUE-5116 [search] Add base API
* 31a87c5 HUE-5116 [search] Split the API outside of the views
* 0b726dd HUE-5670 [editor] Add autocompletion support for Kudu
* cb5c5ef HUE-5669 [responsive] Move search autocompletion to the front
* 657ded9 HUE-5668 [metadata] Hide the search result when show in assist is clicked
* 3c2021e HUE-5667 [metadata] Show assist search results on click
* 588d78b HUE-5666 [editor] Fix JS errors related to popularity in the new autocomplete dropdown
* 2da58fe HUE-5652 [responsive] Only show the assistant for Hive and Impala
* 38d997b HUE-5651 [responsive] Add skeleton for statement details in the right assist panel
* 1f0c41b HUE-5648 [editor] Set focus on the editor after category change in the autocomplete dropdown
* 65bce31 HUE-5662 [assist] Show the selected function description below the functions in the assist panel
* 09369d1 HUE-5631 [editor] Show details about the UDFs in the autocomplete dropdown
* df045ca HUE-5658 [metastore] Ignore error popup when the table is not associated to metadata
* 004c39c HUE-5658 [libsentry] Perm checker returns a generator of results
* e238410 HUE-2981 [search] Disable prefix parameter because of numeric fields
* ed3ed19 HUE-5656 [importer] Keep wizard headers fixed
* 5d74cc9 HUE-5663 [core] Correct bottom border of the user dropdown when no dropdown is there
* d7eb6ec HUE-5664 [importer] Avoid going on a single line for destination name
* 92f7bfc HUE-5618 [home] Use doc name while exporting individual docs
* ec115a6 HUE-2981 [search] Avoid error when un-nesting children documents
* cf0b768 HUE-5632 [editor] Show table comments in the autocomplete dropdown details panel
* 9368922 HUE-5650 [responsive] The functions panel should show the functions of the active snippet type
* 192ebee HUE-5649 [responsive] Move function category selection to the front
* 244355d HUE-5634 [editor] Show details on hover in the new autocomplete dropdown
* 11a5572 HUE-5627 [editor] Close the new autocomplete dropdown on outside scroll
* c971cd8 HUE-5629 [editor] Suppress all API errors in the new autocomplete dropdown
* 6073694 HUE-5630 [editor] Let the contents decide the height of the autocomplete dropdown
* c12bf43 HUE-5628 [editor] Fix issue with incorrect highlighting of matched text in the autocomplete dropdown
* 1aed0d8 HUE-5625 [editor] Close the autocomplete dropdown on empty result after typing
* fbe58a8 HUE-5640 [importer] Align better Solr fields
* 9dcd96f HUE-5639 [importer] Add hide/show properties to db field
* 4754ba2 HUE-5638 [importer] Delete column value shouldn't delete the whole row
* 13757bc HUE-5642 [jobbrowser] Fixed logic
* 92c183e HUE-5642 [jobbrowser] Putting a not allowed value on the time filter shouldn't give http 500
* e4489c0 HUE-5641 [jobbrowser] Align correctly the time filtering
* d54e93b HUE-5655 [metadata] Add support for S3 sources
* 66a3d59 HUE-1176 [jb] Adding skeleton for bundle page
* db4e5c9 HUE-1176 [jb] Adding sections to the Workflow page
* 67c1600 HUE-1176 [jb] Allow users to kill their own jobs in HUE when impersonation is disabled
* 9fc2e1e HUE-1176 [jb] Plug-in the YARN kill job
* f6bca99 HUE-1176 [jb] Add properties and counters to Jobs, Attempts and Tasks
* 0323837 HUE-1176 [jb] Task attempt page revamp
* d736ac3 HUE-1176 [jb] Open a Task Attempt operation
* f176112  HUE-1176 [jb] List task attempts of a MR2 task
* b4eefbe HUE-1176 [jb] Prettify the breadcrumb logic
* f17f048 HUE-1176 [jb] Open task of a MapReduce job
* ce291c5 HUE-1176 [jb] List tasks of a MR2 Job
* 067cc25 HUE-5602 [jb] Make start time filter compatible with python2.6
* 6f3a1e6 HUE-5482 Fix failing test_multiple_trash_directories test
* 99eed45 HUE-5637 [importer] Refresh partition column names dynamically after primary keys change
* ed0da1e HUE-5619 [editor] Fix browser search override dark pattern
* b884eee HUE-5635 [importer] Document chooser should be used for queries
* cda612d HUE-5636 [importer] Reduce label size to avoid selectize triggering
* b31f95a HUE-7 [metastore] Unify Kudu partitions default values and auto add them if needed
* 9dd16c8 HUE-7 [importer] Do not show default data in manual create table
* 7106f8b HUE-7 [importer] Basic table comment input
* c7c3207 HUE-7 [importer] Add default string to the key of maps
* 46ed47a HUE-7 [metastore] Automatically prompt for partition when using Kudu format
* f2a9eda HUE-7 [importer] Set hasHeader logic to depend on source format but then is independent later
* 4c6f20b HUE-5626 [editor] Fix Firefox JS error in autocomplete dropdown
* db60a5f HUE-1176 [jb] Offer to Fetch non generic application information
* 6128313 HUE-1176 [jb] Try to load and display the graph of a workflow
* dc3e79c HUE-1176 [jb] Basic skeleton to fetch Oozie workflow job logs
* 5421456 HUE-1176 [jb] Add specific MR properties to the MR template
* 118b94a HUE-1176 [jb] Basic skeleton to fetch MR job logs
* 8b91748 HUE-1176 [jb] Basic breadcrumb navigation
* f78ade2 HUE-1176 [jb] Adding new overall layout for apps
* 99c395c HUE-5617 [editor] Add colors for each suggestion category in the autocomplete dropdown
* ca47638 HUE-5598 [editor] Introduce selectable categories in the header of the autocomplete dropdown
* 459dda9 HUE-5597 [editor] Skeleton for details area in autocomplete dropdown
* 2038924 HUE-5599 [editor] Show a spinner inside the autocomplete dropdown when it’s loading suggestions
* 4e9471c HUE-5623 [importer] Show column and data samples on the import preview
* 6e4458a HUE-5620 [importer] Style maps, arrays and structs
* 8bdd508 HUE-5624 [importer] Re-introduce bulk edit for column names
* de1cf6e HUE-5622 [importer] Non-guessed field types should default to string
* 86ead14 HUE-5621 [importer] Changing step should reset the vertical scroll
* 5ee44b4 HUE-5616 [oozie] Enable oozie backend filtering by default
* 366fb7f HUE-5562 [core] Installing pig samples gives an error
* 6f827c4 HUE-5590 [importer] Styled Kudu partitions
* bf41885 HUE-5614 [responsive] Prettify the new batch notification
* 9d60e44 HUE-5615 [metastore] Drop a table shouldn't throw a JS error
* 73cb926 HUE-5596 [editor] Add popularity to tables in the autocomplete dropdown
* ee58ec0 HUE-5595 [editor] Add popularity of columns to the autocomplete dropdown
* bad553e HUE-5601 [editor] Add popular filters to the autocomplete dropdown
* 6109918 HUE-5533 [home] Improve home page load time
* bc36557 HUE-1176 [fb] Submit and monitor HDFS archive extraction and offer to open destination
* 25df370 HUE-1176 [indexer] Use the task submission when in responsive
* 7f21f15 HUE-1176 [jb] Open notification in notification panel
* 3375f75 HUE-1176 [jb] Display notifications in live
* fd8254b HUE-7 [editor] Basic export to table name validation
* b82b07b HUE-5602 [jb] Make date filter more user friendly
* 31d1336 HUE-5590 [importer] Fixed add partition
* af8f44d HUE-7 [editor] Validate new table and database names
* 8162a6f HUE-5590 [importer] Restyled normal partitions
* 57ba982 HUE-5590 [importer] Support for comma separated column names paste directly into the field list
* 0fc5d3f HUE-5590 [importer] Cleaned up hasHeader and import column names
* 735e57c HUE-5590 [importer] Workaround a very weird bug
* 6d7b633 HUE-5590 [importer] Allow to remove columns in manual mode
* 19c38cf HUE-5607 [metastore] Selecting varchar instead of string is ignored in create table wizard
* 954f899 HUE-5590 [metastore] Do not show the source type when coming from metastore
* 46ddeba HUE-5590 [importer] Inlined forms
* cae4733 HUE-5590 [importer] Removed duplicated Ids
* 8c1b943 HUE-5590 [importer] Fixed file type selectize
* bbf19cd HUE-5590 [importer] Fixed layout of the second step and moved knockout-selectize to Hue js
* 023758e HUE-5590 [importer] Fixed outputFormat variables typo
* 5d9cbec HUE-5590 [importer] Added truncatedText binding and put it on the data preview table
* 3d48a64 HUE-5590 [importer] Added support for openOnFocus on the filechooser binding
* 25fe089 HUE-5590 [importer] Fixed layout of the first step and top wizard
* d76e380 HUE-5613 [fb] Set output path outside shell script for extract batch job
* 3543f0c HUE-5609 [core] Create a jHueScrollLeft plugin
* 52a12ca HUE-1176 [jb] Componentize task submition and follow-up
* 0a1ae28 HUE-1176 [jb] Display task history in the top right corner
* f0253a7 HUE-5594 [editor] Add popular group bys and order bys to the autocomplete dropdown
* 3cb54f0 HUE-5593 [editor] Add popular aggregate functions to the autocomplete dropdown
* 44b55b0 HUE-5600 [editor] Add popular join conditions to the autocomplete dropdown
* ced4f38 HUE-5592 [editor] Add popular joins to the new autocomplete dropdown
* 5b125fb HUE-5591 [editor] Don’t show the autocomplete dropdown when there are no suggestions
* b241855 HUE-5588 [editor] Add hdfs paths to the autocomplete dropdown
* c9034b1 HUE-3294 [metadata] Avoid error when search returns the HDFS root directory
* a1aac29 HUE-7 [assist] Add create new table link to assist
* 6a5f006 HUE-5606 [assist] Default sorting to creation order
* 3e9c2d7 HUE-7 [metastore] Avoid js error when adding a new partition
* a65a90c HUE-5605 [metadata] Do not enable if desktop auth_password is set
* 218b1ac HUE-5604 [core] Update localization for de, es, fr, ja, ko, zh
* d1334da HUE-3228 [impala] Avoid erroring when opening non existing table
* db693e7 HUE-1176 [jb] Iteration on the design of the single page app
* bf981c0 HUE-5603 [search] Avoid 500 when fixed dates are not specified
* a17df92 HUE-5553 [metadata] Add hook for API to check syntax
* 2996c4b HUE-1176 [history] Skeleton to display submitted tasks in the UI
* e3a9267 HUE-5602 [jb] Add start time filter in jobs page
* a79aaab HUE-5482 [home] Fix failing multiple home/trash tests
* ceac01a HUE-5587 [editor] Add databases to the autocomplete dropdown
* 5241edc HUE-5116 [solr] Allow indexing of records with missing fields
* 28411f4 HUE-2142 [editor] Offer exporting query result in a scalable way
* af1fb7e HUE-5116 [search] Get number of buckets in range facets
* 48b8f3c HUE-5578 [core] Move correct imports into common header footer template
* 279b475 HUE-5116 [search] Support basic indexing in Solr 6 non cloud
* 18a5ca0 HUE-2142 [editor] Change result download truncation limit to be a number of rows
* af1e8c1 HUE-2961 [indexer] Skeleton of quick indexing of SQL query
* 8738a81 HUE-2961 [editor] Backend skeleton for quick indexing of SQL data
* cdbeb85 HUE-2559 [jb] Experimenting with addition of History in responsive menu
* 81e45a4 HUE-5576 [search] Redraw the result grid when toggling all the fields
* 65ccc29 HUE-2961 [editor] Direct link to export SQL result to Dashboard
* 0633583 HUE-5585 [core] Unified scrollbars colors
* a6a1984 HUE-5585 [core] NiceScroll should have a darker scrollbar
* c84b768 HUE-5584 [core] jHueHorizontalScrollbar should have a darker scrollbar
* a43e7ed HUE-5583 [responsive] Support for history and popState
* 48b451f HUE-5586 [editor] Add samples and column aliases to the autocomplete dropdown
* 94ec5da HUE-5526 [editor] Use the use_new_autocompleter config flag to enable the new dropdown
* 0e7331c HUE-5577 [editor] Add functions, identifiers and common table expressions to the new autocomplete dropdown
* 569b23c HUE-5524 [editor] Add column suggestions to the new autocomplete dropdown
* d435866 HUE-5526 [editor] Have single instance of the new autocompleter dropdown for performance
* 9e121da HUE-5575 [editor] Create autocompleter category for tables
* 5935c5f HUE-5526 [editor] Enable live autocompletion for the new autocomplete dropdown
* 60505c2 HUE-5526 [editor] Handle mouse events in the new autocomplete dropdown
* 8ab1057 HUE-5526 [editor] Add prefix matching and keyboard navigation to the new autocomplete dropdown
* 60c4b4f HUE-5526 [editor] Extract Hue autocompleter component to a separate file
* 9af6355 HUE-5526 [editor] Add key and mouse bindings to the custom autocompleter
* d672171 HUE-5526 [editor] Skeleton for the custom autocompleter dropdown
* ed184ae HUE-5527 [editor] Add autocompleter category for keywords
* 59f565a HUE-5579 [responsive] The file viewer breadcrumbs should point to the right file browser
* dd44d12 HUE-5581 [responsive] CSS of the file browser leaks on file viewer
* aad63aa HUE-5580 [responsive] Landing directly on fileviewer breaks the app
* 6779ac0 HUE-5582 [fb] Get rid of chooser.mako
* 93ec511 HUE-5573 [core] Remove placeholder plugin
* 9f77524 HUE-5578 [core] Fix messages in the common footer
* d09fc7b HUE-5553 [metadata] Use another Python 2.6 OrderedDict in serialize
* c5e1f34 HUE-5553 [metadata] Use a Python 2.6 compatible OrderedDict
* ceed03f HUE-5553 [metadata] Update the lib with missing files
* 50a6662 HUE-5574 [responsive] Unify the header and footer
* fb6b24d HUE-7 [importer] Apply selectize to input file format delimiters
* 07bf2a3 HUE-7 [importer] Add selectize to the output table custom field delimiters
* 7721a28 HUE-7 [importer] Properly warn and hint when creating or importing data to existing tables
* 24136a6 HUE-5553 [metadata] Convert upload from shell exec to Python API
* d3af719 HUE-5553 [metadata] Update API to support uploads
* 7f861bb HUE-5553 [metadata] Move to rest API instead of exec
* 0e9ec14 HUE-5553 [metadata] Add new python API lib
* 4eeff02 HUE-5571 [core] Introduce the window.zoom event
* b2a1a8c HUE-5570 [editor] The chart limit change logic in the case of pivoting
* 139a24b HUE-3294 [responsive] Apply the same width to the compose icons
* 4c5970d HUE-5569 [spark] Add "Spark Conf" param to Spark session config dropdown
* 22b2df9 HUE-3294 [responsive] Clearer icon for dashboards
* 6e52e52 HUE-5560 [home] Click and drag to select should start from outside the document list too
* e46b89c HUE-5561 [home] The trash entry shows a tooltip in the top right corner of the screen on opening
* 55ae1d0 HUE-5564 [responsive] The home new document links should open in the same window
* 5e502e5 HUE-5559 [fb] Enter key doesn't act like clicking on 'copy' or 'move' button
* 2b97a72 HUE-5022 [editor] Limit number of items in the chart
* e830925 HUE-5367 [editor] Editor resets vertical scrolling after query is executed
* 0bebebe HUE-5556 [core] Create a customizable SVG logo
* 7881a28 HUE-5558 [responsive] Restyle drop or click button
* 752145d HUE-5555 [core] Create a global drag&drop layer
* 53d5e09 HUE-5554 [editor] The fixed headers should work also with a top banner
* 43a50f3 HUE-5548 [core] Introduce basic Knockout validation
* 13aeb09 HUE-5557 [core] Move to an SVG logo for the Hue topbar
* 2f918e8 HUE-5546 [responsive] Avoid horizontal scrolling on the editor
* 28da8e3 HUE-5544 [editor] Improve reliability of the log panel resizer
* b33c337 HUE-4583 [editor] Add autocompletion of IMPORT and EXPORT statements
* 108545a HUE-7 [metastore] Add a click or drag & drop message for file path
* 1808d8e HUE-7 [metastore] Nested types SQL logic in the backend
* 47566ac HUE-5551 [metadata] Perform Sentry based filtering on searched objects
* 925e11c HUE-5551 [metadata] Sentry for optimizer filtering on database page
* 0e3f617 HUE-7 [metastore] Nested types SQL logic in the frontend
* 91cdb5f HUE-7 [metastore] Remove hard dependency on Solr
* a0ee046 HUE-5552 [editor] Japanese improvement for new SQL Editor #466
* c4ccf9a HUE-5541 [fb] Create visual hints for file and folder operations
* d2ed8f5 HUE-5549 [core] Make max length for a newly created Selectize value customizable
* 740a6d1 HUE-5547 [core] Introduce Knockout maxLength extender for a field
* cfe65bb HUE-5545 [core] The filechooser path should never go to a new line
* 3169f52 HUE-5542 [responsive] The file chooser not always shows up
* 36851b4 HUE-5521 [editor] Update to use get_ordered_interpreters
* 5705bad HUE-5129 [metastore] Backend to propose Kudu column properties like primary keys
* e446cb9 HUE-5129 [metastore] Properly browse Kudu tables from metastore
* f777306 HUE-5129 [metastore] Add Kudu HASH partitioning SQL generation
* 35074bd HUE-7 [metastore] Generate partitions in the backend
* e6b895b HUE-5521 [desktop] Add generic command to override values in hue.ini using a JSON document (#464)
* d744c47 HUE-5478 [notebook] Allow users to specify interpreters on Notebook selection wheel (#461)
* 232903e HUE-5169 [spark] cannot spark submit jar or python
* b3cab65  HUE-7 [metastore] Add support for creating manually a table
* b4780b7 HUE-7 [metastore] Add support for creating database via the importer
* 5d8b5e5 HUE-7 [importer] Add support for creating manually a database
* 639fbd8 HUE-7 [metastore] Add success url to open the table page after the creation
* dc96714 HUE-7 [metastore] Integrate new create table from a file in metastore
* d7d5c04 HUE-5484 [responsive] Make the full menu items clickable
* 2d512fa HUE-5537 [editor] The HDFS path autocomplete shouldn’t cache values
* 46edbcf HUE-5540 [editor] Fix JS error on pivot chart
* 3b40717 HUE-4908 [metastore] Add kudu flag to test mock tables
* 5e6b721 HUE-5484 [responsive] Embeddable create table
* 59da393 HUE-5129 [metastore] Table partitioning frontend
* 3fdf377 HUE-5129 [metastore] Kudu partitioning frontend
* 1ce47ed HUE-5539 [editor] Temporary disable error message on fetch_result_size
* 2d926bd HUE-7 [metastore] Notion of nested type in the frontend
* abe9354 HUE-7 [metastore] Create Hive json table
* f4c133f HUE-7 [metastore] Add Kudu as a supported table output format
* a73e10e HUE-7 [metastore] Connect frontend to backend for table creation wizard
* 02163dd HUE-4908 [metastore] Support computing stats for Kudu tables
* bd5712a HUE-4908 [metastore] Remove notion of HDFS for Kudu tables
* 549dc6d HUE-4908 [metastore] Fetch table properties to confirm that this is a Kudu table
* c001d10 HUE-4908 [metastore] Support displaying Kudu tables
* 49fc79f HUE-5129 [metastore] Backend for providing create table as Kudu option
* 1858ecd HUE-7 [metastore] Make create table wizard genric
* 842ac35 HUE-7 [metastore] Skeleton of create table wizard redesign backend
* 224fe94 HUE-7 [metastore] Skeleton of create table wizard redesign frontend
* 5c5be06 HUE-5508 [fb] Give complete path when copying local script file to HDFS
* 6e2aa77 HUE-5516 [responsive] Embeddable indexes
* 7bcffbd HUE-5515 [responsive] Embeddable collection list
* db9d06a HUE-5517 [core] Improved UX of the auto logout modals
* e8ca96f HUE-5517 [core] Better logout and idle session timeouts messages
* e1aa39c HUE-5528 [responsive] Remove type URL parameter when navigating away from the editor
* 078794e HUE-5522 [fb] Often get mis-aligned HDFS breadcrumbs on filechooser the first time
* fd62d08 HUE-5530 [responsive] Remove multiple bindings on the same element
* 0eedf0d HUE-5529 [core] Remove JS error on Jasmine runner
* 93c50ee HUE-5519 [fb] Clicking on New dir or New file bananas the #url
* 2d0709e HUE-5117 [hbase] Only apply actions on the filtered selected tables
* c663d0e HUE-5245 [editor] Bump the darkness of placeholders and disabled snippet actions
* c0e8652 HUE-5520 [editor] Only fetch result size on SQL statements that are not DDL
* 340cfae HUE-5518 [fb] Bubble up errors from forbidden actions
* 32a8dde HUE-5100 [hbase] Swap Codemirror to Ace
* 1b623af HUE-5513 [responsive] Metastore shouldn't change the url
* 8aaeb0d HUE-5514 [editor] Clear old marked words when opening the context popover
* 9221bb1 HUE-5437 [editor] Don’t show context tooltip when hovering outside the editor text
* c50cffe HUE-5510 [responsive] Embeddable indexer
* b031155 HUE-5111 [responsive] Report and editor mode should work together
* 49a503d HUE-5512 [responsive] Report mode shouldn't change the url
* 4e62dc8 HUE-5482 [home] Handle multiple home/trash directories by merging them into one.
* ccfb831 HUE-5491 [metadata] Upload stats for columns of tables
* a8fd198 HUE-5491 [metadata] Upload stats with number of rows of a table
* 50514f4 HUE-5502 [responsive] Embeddable report
* 054030d HUE-4578 [editor] Add autocompletion of GRANT and REVOKE statements
* 80b95a2 HUE-5116 [search] Support of dimension N of Gradient Map
* 2a883cf  HUE-5116 [search] Support of dimension 1 of Gradient Map
* b179dc1 HUE-5116 [search] Number of buckets for 1 dimension
* e83f1a2 HUE-5116 [search] Add n dimension to the timeline widget
* 4b426a3 HUE-5116 [search] Add analytics grid to the timeline
* fe293b3 HUE-5116 [search] Add analytics timeline to the widget
* b8cb6a6  HUE-5116 [search] Allow to switch between pie and bucket widget type
* 7ab8e2f HUE-5116 [search] Add grid to pie2 widget
* 77bee32 HUE-5116 [search] Unify the grid of grid result and facet
* 0809782 HUE-5116 [search] Properly add back the computed on the facets when loading dashboard
* 42edf92 HUE-5417 [search] Provide the field analysis link
* cd4c5c9 HUE-5417 [search] Manage counts from each dimension
* cc9ab2f HUE-5417 [search] Grid layout scroll bar is showing up sometimes for no reason on Chrome
* b0b0413 HUE-5417 [search] Support displaying nested facet as a grid
* d7094ee HUE-5417 [search] Support result sorting for nested widgets
* 0be5501 HUE-5417 [search] Support toggle all fields logic
* dad32c9 HUE-5417 [search] Add field list to the grid facet
* d5cb9b4 HUE-5417 [search] Add basic pagination to nested facets
* 01a60ff HUE-5325 [search] Skeleton of generic nested grid widget
* 6881f3f HUE-5116 [search] Convert facet data to a data table
* 26fa81f HUE-5116 [search] Integrate sort on text facet of 2 dimensions
* 476ca88 HUE-5116 [search] Display aggregates on dimension 2 even if dimension 1 has some aggregates
* da5ba80 HUE-5116 [search] Support N dimension with aggregates
* e854665 HUE-5500 [responsive] Embeddable oozie bundle editor
* 7d4ac88 HUE-5499 [responsive] Embeddable oozie coordinator editor
* f918020 HUE-5501 [responsive] Fix all the editor links
* b90b7ef HUE-5505 [editor] Fix JS error on sqoop1 type and add placeholder
* c82ab28 HUE-5459 [editor] Improve autocomplete keyword completion around ANALYZE, COMPUTE and INVALIDATE
* aeff61e HUE-5459 [editor] Improve autocomplete keyword completion around DESCRIBE
* 04984bb HUE-5492 [assist] Fix assist refresh
* 0134659 HUE-5475 [editor] Add autocomplete support for partial UDFs
* 1ecc4b3 HUE-5491 [metadata] Gather Hive table stats
* e2a570b HUE-5498 [editor] Fix the CSS problems with report mode
* 5d8ea5c HUE-5497 [editor] Fix JS error on type jar
* 8db223b HUE-5496 [responsive] Changing editor type should affect the currently selected editor snippet
* 922637a HUE-5495 [responsive] The compose dropdown should load apps in the content area
* aa7a04a HUE-5493 [responsive] Create URL entry points for loading specific apps at startup
* e8dc807 HUE-5494 [core] Support for changing a URL parameter
* 57f3ad4 HUE-4704 [security] Fixed Arbitrary host header accepted in Hue
* b8a5146 HUE-5477 [metadata] Make metadata cache conditions more modest
* f338dfb HUE-5481 [editor] Add a flag for background complexity check
* c4edeba HUE-5843 [jobsub] Avoid multiple list calls and fix JS error when deleting all the jobs
* 5e9f442 HUE-5488 [responsive] Correct the file view page styling issues
* 3e2169f HUE-5489 [responsive] Fix jHueNotify
* 7271ff1 HUE-5490 [responsive] The Filebrowser list page shouldn't have a global bottom bar
* 451e59d HUE-5449 [editor] Fix for JS error on autocompletion of popular order by columns
* b780ba1 HUE-5469 [editor] Check Hive query complexity in the background
* fe13e5b HUE-5474 [core] Knockoutify the left nav in responsive
* ef2d74c HUE-5476 [core] Fix TTL is_idle middleware check
* 785a149 HUE-5470 [responsive] Drop files should not overlay with other menu items
* d75ad26 HUE-5354 [fb] Edit file shouldn't refresh the page
* 04ab581 HUE-5468 [editor] Sort autocompleter table suggestions by popularity
* 0463fc6 HUE-5472 [home] Fix rendering of the SVG icons and labels in embedded mode
* ee54c97 HUE-5471 [home] Remove navbar header in embedded mode
* 998e98b HUE-5473 [home] The default view does not render all the list items
* 9c393b7 HUE-5464 [search] Marker map legend output is very large
* 83a395e HUE-5457 [fb] The edit file 'save as' should display better the filechooser
* 56197c7 HUE-5458 [core] Embed S3 browser in responsive
* 908b448 HUE-5447 [assist] Use the autocomplete timeout for fetching popular tables
* 6275cab HUE-5467 [assist] Fix and improve styling of functions panel
* 69261c9 HUE-5466 [core] Fix JS error in responsive
* 508cde8 HUE-5455 [fb] Previewing a file shouldn't refresh the page on file viewer
* 6f181a8 HUE-5456 [fb] The file edit save button should submit via AJAX
* c074a61 HUE-5443 [metadata] Remove with instruction which is not Python 2.4 compatible
* 2600bdc HUE-5465 [fb] Autoconfigure to enable S3 browser if IAM role being detected
* c2fdce2 HUE-5443 [metadata] Uncomment the skipping of tests when the lib is not configured
* f12d9a3 HUE-5443 [metadata] Convert to Python 2.4 the temporary file creation
* d13c67b HUE-5325 [core] Revoke S3 access permissions to default group
* f5a184d HUE-5448 [editor] The autocompleter should fetch columns in parallel to top columns
* 1ba9259 HUE-5446 [assist] Include hostname in cache identifier
* eeb549e HUE-5451 [metastore] Fix js error in the create database wizard
* 5634fb4 HUE-5445 [assist] Enable shift-click on refresh to clear all caches
* 01c6f85 HUE-3294 [core] Add reports to Compose menu
* b05fd80 HUE-5443 [metadata] Upload history according to the editor type
* 3ac3073 HUE-5443 [metadata] Option to only load the last 10 query history for dev purposes
* a548b0d HUE-5443 [metadata] Show basic progress of the history upload
* ce4f527 HUE-5443 [metadata] Upload proper query id and execution time
* 358968b HUE-5443 [metadata] Switch uploading to propose the format in json
* 37e24e9 HUE-5353 [fb] Switching between text and binary mode on view page shouldn't refresh the page
* 44d9e20 HUE-5454 [fb] Speed up binary rendering of the file viewer
* 9f70650 HUE-5453 [fb] The file viewer refresh button shouldn't reload the page
* 233c0d5 HUE-5452 [fb] Remove lazy loading of pages from the file viewer
* b8196c8 HUE-4870 [assist] Open HDFS assist on home of the user by default
* 7518481 HUE-5444 [assist] Only fetch popular tables for open databases
* cbc781c HUE-5438 [editor] Offer to hide the query cancel message
* 6d8491c HUE-5272 [search] Warning messages when performing migrate (fix in libsolr)
* 16dede5 HUE-5435 [notebook] Allow dbproxy classpath to be configurable (#458)
* fc086db HUE-5442 [core] Add missing TTL import in responsive
* 3855945 HUE-5442 [assist] Introduce separate cache timeout for metadata
* 024e6a3 HUE-5430 [assist] Prefetch popularity of tables
* 8292ddd HUE-5430 [assist] Fix sort order for popular sort
* 1f9473f HUE-5430 [assist] Use default sort for equally popular entries
* 508847a HUE-5441 [fb] Add the fileviewer to responsive
* 2bb9c18 HUE-5352 [fb] KOify the view file page
* bb35a40 HUE-5440 [home] Extract common home for normal and embeddable homes
* 9cee7e0 HUE-5430 [assist] Switch sort icon to spinner when calling the API
* 78161bf HUE-5430 [assist] Add popular sorting of tables
* 1ab5321 HUE-5428 [assist] Add standard sorting options for DB assist
* 4e4b957 HUE-5413 [home] Remove underlined links in IE
* 9916b2b HUE-5296 [fb] Allow GETTRASHROOT to be called on full file path
* 88dd96a HUE-5436 [fb] Fail elegantly if CHECKACCESS is not supported and returns a 400
* 51e2624 HUE-5420 [aws] Support alternative s3 endpoints (#455)
* 8401c82 HUE-5275 [libsentry] Privilege checker should return filtered list of the original objects
* c93405e HUE-5426 [fb] Disable drop from assist to the file list
* dd09139 HUE-5425 [fb] History click should load via AJAX
* 230c87d HUE-5427 [fb] The drop functionality shouldn't refresh the page
* 4a637d9 HUE-5433 [core] Add startsWith, endsWith and includes string polyfills to hue.utils
* 45fd138 HUE-5429 [useradmin] Creating a new user gives a AttributeError: 'User' object has no attribute 'user'
* 651e027 HUE-5418 [aws] Support automatic configuration when IAM metadata is present
* c154c13 HUE-5272 [beeswax] Warning messages when performing migrate
* abbd723 HUE-5424 [fb] Embed file list in responsive
* 3bb2d36 HUE-5416 [assist] Fix document panel styling
* 9b85463 HUE-5414 [assist] Improve filter styling and positioning
* 4ea6ea6 HUE-5333 [assist] Fix context popover in responsive
* 5cc3d6f HUE-5422 [editor] Improve defaults chart values for marker maps
* 4fca062 HUE-5421 [editor] The default X and Y for the charts should never refer to the same column
* 03b22f4 HUE-5423 [search] Bar charts are wrongly rendered when passing from no data to data available
* a4beea2 HUE-5415 [metadata] Rename client command
* 7b68581 HUE-5415 [metadata] API Skeleton to poll for upload status
* 4facc9b HUE-5340 [search] Remove additional escaping as we already do it in make_field
* f39ca99 HUE-5382 [fb] Rename S3A to S3 in FileChooser
* 67ec63d HUE-5412 [editor] Integrate skeleton of similar query suggestion API
* 892b5c7 HUE-5411 [editor] Integrate skeleton of query history upload
* 889b490 HUE-5363 [fb] Restore from trash form should submit via AJAX
* 7583992 HUE-5398 [fb] Empty trash form should submit via AJAX
* 0ea0d74 HUE-5361 [fb] Change owner form should submit via AJAX
* 3ba2257 HUE-5360 [fb] Change permissions form should submit via AJAX
* 637fdaa HUE-5359 [fb] Move file form should submit via AJAX
* 8cdf822 HUE-5358 [fb] Rename file form should submit via AJAX
* 3ff72e6 HUE-5407 [search] Bar charting of grid result can get doubled up
* 27d74e5 HUE-5325 [aws] Update test to work even is s3 is disabled
* 1c7a7de HUE-5325 [core] Revoke S3 access permissions to default group
* cd9906e HUE-5325 [fb] Add set of test about S3 permissions
* 7c31aa1 HUE-5325 [aws] Enable S3 browser on only when keys are there
* 5740b5d HUE-5310 [search] Use Doc2 modal in search_controller
* 36b319a HUE-5374 [assist] Increase the context popover min width to prevent tab wrapping
* 002f93a HUE-5375 [metastore] Use tooltips for upper right action icons
* df461b1 HUE-5346 [editor] Add autocompletion of popular aggregate functions
* 4da1696 HUE-5378 [assist] Don’t show the comment header in the context popover when there’s no comment
* 71197b8 HUE-5399 [editor] Banner might hide the right panel
* df0a8c6 HUE-5356 [fb] Create new folder form should submit via AJAX
* 1731c17 HUE-5355 [fb] Create new file form should submit via AJAX
* c29ec5a HUE-5357 [fb] Copy file form should submit via AJAX
* d5d573d HUE-5403 [editor] Download results modal sometimes doesn't close on IE11 or Edge
* f35944b HUE-5404 [editor] Nicescrollify log panel
* 16f60ad HUE-5275 [libsentry] Avoid mutating original objects in privilege checker
* a3c5943 HUE-5340 [search] Escape Solr field that have XSS injection (like <script>alert(1234)</script>)
* f28a06d HUE-5377 [assist] Don’t show the assist link in the context popover opened from the assist
* a9c0bc0 HUE-5380 [assist] Fix right-click context menu in assist for Firefox
* 6b3e775 HUE-5391 [assist] Don’t show query builder when it’s disabled
* 1749cef HUE-5390 [assist] Fix for incorrect column order
* 2f8ddf2 HUE-4447 [auth] Try to ensure the user has a home directory when logging from any backend
* 00d96c9 HUE-4447 [auth] Force create a home directory if a user has a profile with it
* 2e7cab8 HUE-5331 [editor] Fix mousewheel scroll flakiness on the result grid
* 0c7634b HUE-5362 [fb] Delete file form should submit via AJAX
* 7ae7b48 HUE-5397 [fb] Meta clicking on the breadcrumbs should open a new tab
* 980591f HUE-5369 [fb] The trash link shouldn't refresh the page
* 618e338 HUE-5368 [fb] The home link shouldn't refresh the page
* b69fbd4 HUE-5388 [core] Remove index.html link from header
* 8825d08 HUE-5275 [libsentry] Add remaining privilege checker test scenarios
* 3335373 HUE-5275 [libsentry] Add optional key function aren, refactor tests by scenario
* d1eb2e3 HUE-5173 [fb] Fix handling of S3UploadError so that error is caught and displayed
* 83062d2 HUE-5371 [core] Add the region to the filepicker breadcrumbs for S3
* 2203cee HUE-5370 [metastore] Create table from S3 should remove the file from the create table form input when selecting it
* 8eacce4 HUE-5379 [editor] Add autocompletion of Hue variables
* 9b20e98 HUE-5381 [editor] Adjust popular values autocompletion to latest API
* 5e582d5 HUE-5344 [editor] Add autocompletion of popular complete order by clauses
* a9cbe97 HUE-5344 [editor] Add autocompletion of popular complete group by clauses
* 1e4e89b HUE-5372 [editor] The initial gutter of Ace overlaps with the editor text at page load
* 2e8cf8c HUE-5373 [editor] The horizontal scroll handle should be at the end of the result table
* be0f445 HUE-5387 [assist] Rename 'Insert' from right click to be clearer
* 4091530 HUE-5287 [metadata] Add create tenant API
* 5a0fda7 HUE-5343 [metadata] Automatically pull the latest product id if none are specified
* ff8ba65 HUE-5295 [desktop] Avoid microsecond comparison for last_modified field MySQL < 5.6 doesn't support microsecond precision. https://code.djangoproject.com/ticket/19716
* 9efb39f HUE-5339 [search] Multivalued data can include js XSS injection
* 6927305 HUE-5346 [editor] Prepare the parser for suggesting top aggregate functions
* c497518 HUE-5332 [assist] Fix context popover for databases
* 7058b1a HUE-5350 [editor] Improve caching of top filters, joins and columns
* efd9fc1 HUE-5348 [search] General settings can include js XSS injection
* c836437 HUE-5183 [metastore] Improve import data modal
* 1bd206a HUE-5364 [fb] The S3 and HDFS history items shouldn't be displayed up together
* c4cc512 HUE-5349 [search] Query definitions can include js XSS injection
* 30e9161 HUE-5345 [editor] Add editor autocompletion of popular filters
* 781eef2 HUE-5344 [editor] The autocomplete parser should suggest complete order by, group by and filter
* 700d27e HUE-5335 [assist] Show function description as tooltip
* 16bdac1 HUE-5337 [editor] Autocompletion of top columns should take tables and databases into account
* c45bf50 HUE-5321 [assist] Add a toggle to the functions filter
* 94a942e HUE-5336 [editor] Fix autocompletion UDF weight issue
* 455637c HUE-5334 [editor] Prioritize top columns in select, order by and group by suggestions
* cabae26 HUE-5334 [editor] Prepare ApiHelper for autocompleter top column suggestions
* 8ca1af2 HUE-5334 [editor] Add source to autocompleter suggest columns details
* 1d77f77 HUE-5202 [fb] Add bash shebang in the extract script
* fa71a94 HUE-5279 [oozie] Add ENABLE_OOZIE_BACKEND_FILTERING param to support previous oozie versions
* 64533ac HUE-5279 Bundle text filtering should call oozie rest API to display jobs list
* 2e6ce60 HUE-5279 Coordinator text filtering should call oozie rest API to display jobs list
* e4eb56d HUE-5279 Workflow text filtering should call oozie rest API to display jobs list
* ef0c021 HUE-5317 [assist] Remove duplicate error lines when opening a table fails
* 228b189 HUE-5315 [editor] Fix issue where the SQL parser counts CRLF as two lines
* 5e7748c HUE-5316 [assist] Fix context popover for views
* 0422d56 HUE-5314 [editor] Add support for multiple tables in join autocompletion
* 5054bc8 HUE-5320 [editor] Resizing the editor should hide the fixed header and then redraw it
* 8cc088c HUE-5319 [editor] The close expanded mode overlaps with the snippet help icon
* 591dbce HUE-5318 [editor] Clicking on the labels on snippet settings should add properties
* 68acdd7 HUE-5327 [core] Stop blurring after session expiration when the modal in closable
* 480dc29 HUE-5322 [fb] Moving/Copying a folder in S3 results in duplicate children files at target
* 091e9ff HUE-5311 [metadata] Basic display of query recommendation
* 3724856 HUE-5238 [editor] Swap position of legend and value in the pie chart
* 35d42f0 HUE-5309 [editor] The autocompleter should use table aliases in join suggestions
* 8edf6ae HUE-5312 [core] Typo in ktrenewer error message
* 7c4c43c HUE-5280 [search] Style the query definition title in the page
* d50f146 HUE-5293 [security] Fix DOM blur for logout modal
* 97c000c HUE-5301 [search] Fix DOM blur for logout modal
* 6381d72 HUE-5313 [assist] Add search to functions panel
* cbaf4c3 HUE-5298 [editor] Show readonly editor just after the file or document has loaded
* 923c791 HUE-5307 [metastore] Fix double assist toggle buttons
* 928c6e4 PR447 [oozie] Update the tests with the cleaner escaping of workflow names
* afc3ea2 HUE-5295 [desktop] Do not change the last_modified field when migrating history queries
* 1a3c5db HUE-5308 [editor] Autocompleter should not suggest the active database in joins
* ad2326a HUE-5305 [home] Fix empty share document modal and improve sharing UX
* 140d307 PR448 [notebook] Catch missing 'snippets' field in document2 data in hive_server2_lib
* 50bec63 PR447 [oozie] Fix non-English workflow name mangling problem
* 4e4b15d HUE-5303 [editor] Avoid XSS in the viewmodel options
* 2e49b22 HUE-5299 [editor] Fix js error on the list of notebooks
* 4bb4e2c HUE-5292 [about] Correct alignment of the logs checkboxes
* 466a72d HUE-5300 [oozie] Workflow detail page has a js error
* 91e0d12 HUE-5290 [search] Empty collections landing page for admin is misleading
* c34f870 HUE-5302 [core] Disallow new line in the x-editable binding
* 829b612 HUE-3294 [search] Bubble-up Solr exception in case of 500
* aa42371 HUE-3294 [search] Avoid 500 error in typo in string substitution
* fd76a88 HUE-3294 [search] Do not show input function for non function like field
* b04096f HUE-5284 [notebook] Refactor to include file snippet in notebook too
* e9b1a07 HUE-3294 [core] Adding more links in the menu
* 3b32792 HUE-3294 [search] Add metric functions to the nested facets
* 6c102c5 HUE-3294 [core] Move left nav behind top nav
* 0701566 HUE-3294 [assist] Show the assist visibility toggle on hover
* dacb747 HUE-3294 [assist] Style the functions dialect drop-down
* 2847a7c HUE-3294 [editor] The Hue logo is now smaller and with a prettier trunk
* 4ca8227 HUE-3294 [editor] The Hue logo should point to the home page
* 3882409 HUE-3294 [core] Replace the top nav logo with svg version
* a207172 HUE-3294 [assist] Use hue-drop-down for SQL snippet source type
* c2ee67d HUE-3294 [assist] Use hue-drop-down for function dialect selection
* fae127e HUE-3294 [jobbrowser] First pass of integration of the workflow editor with the new layout
* 61f96a8 HUE-3294 [core] Convert snippet-db-selection ko component to a generic hue-drop-down
* c85fc62 HUE-3294 [core] Move knockout scripts to common header
* 11d4c11 HUE-3294 [editor] Add border to top bar
* f4bae0f HUE-3294 [core] Default to the editor
* 930cfb6 HUE-3294 [editor] Drop the background on the top bar
* 418b691 HUE-3294 [assist] Add tabs to the right assist
* ee13345 HUE-3294 [oozie] First pass of integration of the workflow editor with the new layout
* 6d23bd1 HUE-3294 [search] Integration with the new layout
* a440175 HUE-5275 [metadata] Add correct db-table list format to top-aggs
* 8021d58 HUE-3294 [search] Add support for add, sub and ms functions
* f18cd5d HUE-3294 [search] Add form to support percentiles aggregates
* 71e334a HUE-3294 [core] Better caching of CSS and JS files
* 038841b HUE-3294 [notebook] Remove create new query option from execute dropdown
* b29b996 HUE-3294 [search] Support multiplication in aggregate functions
* 0c3382a HUE-3294 [search] Add more than one dimension to formula widget
* ef20fe9 HUE-3294 [core] Add drop target in left nav menu
* e4f2c9d HUE-3294 [assist] Extract functions panel
* 498d455 HUE-3294 [core] Fixed missing variable from augmentHtml binding
* e6105c7 HUE-3294 [editor] Removing globally the nv.d3 debug infos
* 421016f HUE-3294 [editor] Avoid reloading the same CSS and JS files
* 41deff4 HUE-3294 [assist] Add the pig functions to the assist
* b8ce8cd HUE-3294 [editor] Caching and switching of apps
* 80595b7 HUE-3294 [editor] Made table result scrolling work in embedded mode
* 04c3cd5 HUE-5275 [metadata] Perform basic Sentry SELECT filtering on tables
* 26c95d1 HUE-3294 [core] Add missing css file where assist is used
* 5d3494e HUE-3294 [editor] Improved integration CSS
* fee331c HUE-3294 [core] Adjust SQL functions categories in the assist
* 9ddcf04 HUE-3294 [core] Initial styling of the functions list in the right assist
* 1df8bf0 HUE-3294 [search] Avoid null pointer on function subscribe
* 97166bd HUE-5294 [editor] Extract reusable styles from the context popover
* 45de9ff HUE-3294 [search] The new facet toggle shouldn't be displayed vertically
* 5d029b1 HUE-3294 [metadata] Support db-table-list in top columns and filter
* 454dcd8 HUE-3294 [search] Add nested metric format instead of single function
* 8a205f0 HUE-3294 [search] Improved style of the datepicker
* b6d04a2 HUE-3294 [core] Skeleton for function categories in the right assist panel
* 8b48efc HUE-3294 [core] Add skeleton for functions in right assist panel
* 409ef93 HUE-3294 [search] Fix JS error on the search viewmodel
* 16a4d02 HUE-3294 [core] Add more spacing between alternatives in the the left nav
* e80caf3 HUE-3294 [core] Switch left menu to overlay and add some initial content and styling
* 847894c HUE-3294 [core] Customize the hamburger icon
* 8e481c7 HUE-3294 [search] Added selectize to the field chooser
* a6bb96e HUE-3294 [core] Slightly increase the size of the assist top buttons
* ce994db HUE-3294 [search] Better styling for the help of timepickers
* bb25b94 HUE-5291 [editor] Only autocomplete joins when possible
* fab229f HUE-5291 [editor] Add complete join suggestions to the autocompleter
* 42cc01a HUE-3294 [search] Hide spinner after a partition chart has been rendered
* 9daee3a HUE-3294 [search] Fixed clearfix for new facets
* 6552ddf HUE-3294 [search] Fixed clearfix for facets
* cafa153 HUE-5287 [metadata] Add API for top columns autocomplete
* ab14ffe HUE-5287 [editor] Suggest popular join conditions in the editor
* 98ed961 HUE-5289 [editor] Add hash as cache identifier option to the api helper
* d9fd92e HUE-3294 [metadata] Add top databases API
* 3177441 HUE-3294 [core] Added nv.d3.sunburst and new nv.d3 utils
* d675955 HUE-3294 [core] Upgraded d3 to the latest
* e805d63 HUE-5288 [editor] Pressing enter key on the export results modal shouldn't open a file chooser
* 5307449 HUE-5287 [editor] Add join condition suggestions to the autocomplete parser
* 8982c5d HUE-3294 [core] Add skeleton for jobs dropdown
* 3a271ce HUE-3294 [home] Combine document and metadata search in general search
* 9a92cf0 HUE-3294 [search] Simplify complex aggregated functions
* 87f1e6b HUE-3294 [editor] Improved style of a readonly editor for a file type
* ec00b8d HUE-3294 [Editor] Improved style of a readonly editor
* e60903f HUE-3294 [oozie] Converted to documentChooser binding
* 8fa499e HUE-3294 [editor] Added documentChooser binding
* 5712b2c HUE-3294 [core] Make top nav buttons a tad bit lighter on hover
* c9d214d HUE-3294 [core] Style the top right nav admin menu
* d8b90d0 HUE-3294 [core] Style the top right nav actions
* 8760c1a HUE-3294 [search] Add field type in field analysis popup
* 7a952e6 HUE-3294 [editor] Set Ace to readonly if the type is not text
* b995f96 HUE-3294 [core] You can now call hueDebug.viewModel() with a target element
* b4974a6 HUe-3294 [notebook] Retrieve content of document snippet
* fa477b2 HUE-5232 [metadata] Add top aggs API
* 353a3db HUE-3294 [search] Fixed text squeezer
* 729a560 HUE-3294 [search] Improve counter display
* b02c739 HUE-5232 [metadata] Add top joins API
* 942321a HUE-3294 [assist] Friendlier search placeholder
* 892d807 HUE-4866 [editor] Load back the selected document snippet object
* dcabb7b HUE-3294 [core] Add global search autocomplete
* 1534b41 HUE-3294 [editor] Fix typeahead binding
* 1804979 HUE-3294 [core] Shrink the hamburger menu icon
* c7d5a0f HUE-3294 [core] Increase the size of the top nav search bar
* 43097fa HUE-3294 [core] Fix url parameter content detection
* b69e6b0 HUE-3294 [core] Style the compose button
* be7c08e HUE-3294 [core] Style the main search bar
* 4894752 HUE-3294 [editor] First round of adding Search
* b646609 HUE-3294 [editor] Added niceScroll to responsive
* 2228b6a HUE-3294 [editor] Avoid double loading of JS files
* 2e4f250 HUE-4866 [editor] Perform variable replacements in multi query in file queries
* 352c991 HUE-5261 [editor] Smarter row count estimate
* 715125f HUE-3294 [assist] Force loading of the db panel in background
* 6988783 HUE-3294 [editor] Speed up scroll
* e9072f8 HUE-3294 [metastore] Added temporary links to load apps
* db2f17a HUE-4866 [editor] Remember last path on File editor chooser
* 9f2fc43 HUE-4866 [notebook] Execute saved Hive snippet from a notebook snippet
* 31fca1c HUE-4866 [editor] Avoid showing column list on re-execute
* 6df91d8 HUE-3294 [core] Add IE support for responsive flex layout
* 22a689c HUE-4866 [reporter] Fix result table extender
* d907a7d HUE-4866 [editor] Only pole for snippet file content when using a statement from a file
* 605ac93 HUE-4866 [editor] Insert content of text snippet when using query from a file
* ba23d40 HUE-4866 [notebook] Select a document as a snippet
* 5df0612 HUE-4866 [oozie] Refactor out the document selector
* c486023 HUE-3294 [core] Add right side panel and a split draggable binding for flex layout
* e7acec1 HUE-3294 [metastore] Created an embeddable version of the metastore
* b972da5 HUE-2981 [search] Detect and enable nested documents when they are in the collection
* 51a5b6c HUE-3294 [assist] Adding refresh and filter icons to document panel
* 9429861 HUE-3294 [desktop] Add backend document search for documents in assist
* 82baec1 HUE-3294 [core] Renamed also right-panel related variable to content panel
* 5a749a7 HUE-3294 [core] Renamed right-panel to content-panel
* ce628dc HUE-3294 [core] Fix assist panel resizer
* 60f32e6 HUE-3294 [core] Support reloading of editors on responsive
* 71be351 HUE-3294 [core] Add missing styles for assist and context popover to responsive
* c9938e8 HUE-3294 [core] Fix missing imports for results to show up
* c4ca69c HUE-3294 [core] Improved assist panel styling
* 157e47a HUE-3294 [desktop] Move search document and data calls to desktop
* a205827 HUE-3294 [core] Change URLs for notebook.ko
* 3b42f0b HUE-3294 [core] Fix assist toggle
* 15d85fb HUE-3294 [core] Make the editor load completely
* 968a81a HUE-3294 [core] Enable/disable assist in editor_components
* 2873917 HUE-3294 [core] Fix HTML structure
* 52fcfd6 HUE-3294 [core] Added hueDebug to the page
* 6c5e48b HUE-3294 [core] Added editor_embeddable and loader
* 0f3f79f HUE-5297 [beeswax] fixing Open redirect vulnerability in on_success_url
* 40c6c45 HUE-4546 [editor] Cannot execute any Hive query: 'NoneType' object has no attribute 'update_data'
* 07e78ae HUE-5296 [fb] Deleting a file from File Browser should determine the trash dir via getTrashRoots
* e18b270 HUE-5275 [libsentry] Add support for URI in privilege checker
* a899c18 HUE-5275 [libsentry] Add support for Solr (V2) Sentry objects to privilege checker
* 33e491d HUE-5173 [fb] Raise S3UploadError if user does not have permissions to upload
* a396fca HUE-4866 [fb] Submit archives as batch job
* d2dc60b HUE-5275 [libsentry] Add privilege_checker test with mock API response
* 797d6f7 HUE-5275 [security] Enable filtered searching of Sentry objects based on privileges
* 1156463 HUE-5071 [oozie] Import workflow with hive dependency from cluster to another one fail
* ebee925 HUE-5202 [filebrowser] Fix incorrect path while copying script to hdfs
* 02f6180 HUE-5286 [metadata] Taking into account full prefixing of tables and columns
* 9403c35 HUE-5231 [search] Avoid error popup when analysing text fields
* ffc916e HUE-4866 [notebook] Test getting document as snippet source
* 24693ff HUE-5284 [notebook] Refactor to include file snippet in notebook too
* 1d645f8 HUE-5187 [assist] Default showCores to true in Collection if we only have cores
* f5ab2ed HUE-5231 [search] Bump default number of rows in grid result to 25
* 4f9afe3 HUE-5231 Tweaking the responsive menu with new links
* 073fa17 HUE-4866 [editor] Do not able execute from a file when only query string is set
* b043a1e HUE-5282 [editor] Add missing non SQL dialect types
* 1fc42f9 HUE-5282 [editor] Clean-up toggling editor / notebook mode logic
* 5d5a5aa HUE-5284 [notebook] Reset snippet status when switching its type
* 6897617 HUE-4866 [editor] Support extracting query variables from a file
* c4a0c6e HUE-4866 [editor] Support multiquery in query from a file
* f52bc3a HUE-5283 [notebook] Show the top icon
* bc24d45 HUE-5282 [editor] Simplify logic when switching editor modes
* b6be60c HUE-5239 [assist] Don’t trigger search when switching tabs unless search is active
* 64c0fde HUE-5240 [editor] Fix closing of inline search in the tabs
* 508deb3 HUE-5249 [editor] Fix JS error on complex column right click
* 98a198c HUE-5273 [editor] Show additional details in the tooltip for the context popover
* b469242 HUE-5274 [editor] Fix JS error related to comments in the context popover
* 8e6c356 HUE-5231 [search] Avoid js error when nested types are disabled
* f52b2df HUE-5281 [core] Log real user real ip when using a load balancer
* 0977ed6 HUE-5072 [oozie] Non accessible submitted saved workflow errors when opened in dashboard
* 85656f7 HUE-4866 [editor] Unify when a statement isReady() across the snippet
* 79e003d HUE-4866 [editor] Integrate file content into the query statement
* 799bf62 HUE-4866 [editor] Submit query from a source file
* 9c3e942 HUE-5252 [editor] The snippet settings layout should align vertically
* 42fc911 HUE-5237 [useradmin] Use selectize.js for the settings
* 0ceaea8 HUE-5231 [search] Align result grid headers to the left and make them scrollable
* 27c007c HUE-5253 [editor] Improve query time formatting on long running queries
* 39178f4 HUE-5250 [editor] DB selector dropdown is shifted to the left
* 6e7b97e HUE-5251 [editor] The check status call should stop if there's a server problem
* 1065418 HUE-5254 [editor] The result count should be formatted
* 6c43105 HUE-5258 [editor] Timeline charts has a D3 error with a timestamp Y value
* 9f70614 HUE-5277 [oozie] User object in Job may not always be initialized
* 877c2b6 HUE-2981 [search] Inject nested fq only when nested document is enabled
* 989fd65 HUE-5269 [editor] Explain button does not do a use DB before executing
* 50cebf6 PR445 [doc] Update Django version URL to exist
* 2091d3e HUE-2981 [search] Build tree schema in collection property page
* 4365deb HUE-2981 [search] Re-introduce 3rd dimension to the Timeline
* a68c894 HUE-2981 [search] Re-introduce analytics text facet sorting
* 453006d HUE-2981 [search] Provide computed subcounts into the tree data
* 20d30b8 HUE-5224 [metastore] Add complexity to the list of queries
* ea6a6f0 HUE-2981 [search] Add nested facets of dimension > 2
* 22754e7 HUE-5224 [metadata] Add popular joins API
* b523bac HUE-2981 [search] Support nested document faceting
* 8a0827a HUE-2981 [search] Display nested documents of records
* 9fc1daf HUE-2981 [search] Support nested documents display
* a830936 HUE-5141 [core] Home page import document popup should provide information about the import
* 2991ec2 HUE-5174 [fb] Display correct error message when read-only user attempts to create/delete object in S3
* f1dafa8 HUE-5270 [assist] Context popover should handle complex types
* 7d0aeca HUE-5268 [editor] Autocompleter should not suggest columns without tables
* 9db73dd HUE-5234 [editor] Fix JS error related to editor locations
* d9c71f8 HUE-5232 [metadata] Add a search button to nav search
* 03d104e HUE-5236 [editor] Deprioritize virtual columns in the autocomplete suggestions
* ddca8ce HUE-5259 [editor] Scrollbars appear on timeline chart when hovering at right end
* b7bb45a HUE-5256 [editor] Clicking on the Stop button of a snippet doesn’t give any feedback
* e83bc61 HUE-4895 [editor] Name downloaded query with their query name if possible
* 8a713b8 HUE-5260 [editor] Double click on next/previous result search makes the results tremble
* dd70f73 HUE-5257 [editor] Clear up the status bar when a query gets canceled
* 8fb5211 HUE-5266 [core] Fix Jasmine runner
* 4715c1b HUE-5202 Clean up added zip file which is common across tests
* 37e9d3e HUE-5141 [core] Import document popup should provide information about the import
* c403d21 HUE-5202 Use DEFAULT_USER.get() instead of hardcoding hue user
* 31a942d HUE-5202 Disable extract uploaded archive using notebook connector by default
* 0ed940a HUE-5202 Move extract functionality to desktop/lib/tasks/extract_archive
* 7dbd1e6 HUE-5202 Unit test for validating extract_archive_in_hdfs()
* a41b6a6 HUE-5202 Added API to allow archive extraction using Notebook shell connector
* 2bd5af1 HUE-5202 Added shell script that is used in the oozie job for extracting archive
* d49eda0 HUE-5235 [editor] Allow to type any setting in the session tab
* 6a99a2c HUE-5187 [assist] Add show cores only option to the index assist panels
* f81f8d9 HUE-5230 [metadata] Enable ESC to cancel tag editing
* 51bceab HUE-5215 [metastore] Add test for dropping tables with skip trash option
* 9fdeb1e HUE-5215 [metastore] Add skip trash option when dropping table from metastore
* 1ad4b85 HUE-5218 [search] Validate dashboard sharing works
* 28a2a70 HUE-5225 [core] Prevent Oozie and Job Designer duplicate example documents from being installed
* 9c11e66 HUE-5173 [fb] Correctly check READ and WRITE permissions for S3 before upload
* d8df800 HUE-5229 [filebrowser] Improve select all performance
* 03dc9fe HUE-5223 [core] Lighten up the treeview chart
* 592dfc5 HUE-5179 [search] Timeline search is not working after the first select
* 09a325f HUE-5228 [editor] Allow SQL identifiers starting with numeric characters
* 008f74c HUE-5227 [editor] Put exact type match suggestions on top in the autocompleter
* e8a999d HUE-5222 [editor] Move tags to the details tab in the context popover
* d18fec9 HUE-5219 [core] Deleted examples can not be re-installed
* 3ac4d68 HUE-5115 [core] Revert custom job browser connection pooling
* d2d6fbc HUE-5221 [metadata] Show result count instead of autocomplete count in nav search
* 67273fc HUE-5220 [editor] Show comments and various details for tables in the context popover
* 4ed8e7d HUE-5145 [metadata] Adding popular table filters API
* 5dae2bb HUE-5145 [metadata] Adding more information about popular queries and joins
* 11e65b9 HUE-5217 [backend] Resolve LGPL copyleft issue - Paramiko
* 72d2555 HUE-5106 [oozie] Delete on decision node children creates broken links
* efe534d HUE-5213 [metadata] Protect against matching terms with regexp syntax in frontend
* a98815a HUE-5213 [metadata] Protect against matching terms with regexp syntax in search
* 0137696 HUE-5212 [metadata] Harmonize result description display and highlighting
* 3031b2d HUE-5211 [metadata] Support utf8 in search
* a189251 HUE-5167 [core] Improve SASL error reporting in HUE
* 46cdf8d HUE-5153 [aws] Turn off default AWS account when not configured
* 28edd1b HUE-5153 [aws] Allow S3 client to attempt to pickup IAM instance metadata
* d89587b HUE-5165 [impala] Get result count for all select * queries
* ac52b36 HUE-5204 [beeswax] Hide editor links to avoid falling back to old editor when doing a drop/create table operation
* e643aae HUE-5189 [core] Add correct case to the HBase assist entry file
* 85ad692 HUE-5210 [notebook] Reduce snippet icon brightness
* 250fcea HUE-5206 [editor] Show tooltip for active chart type
* 5535aab HUE-5205 [metadata] Fix tag editor js error after multiple edits
* 9be9829 HUE-5203 [assist] Use info icon instead of chart icon for context popover
* 213edf0 HUE-5200 [editor] Empty assist on first page load
* 17f7988 HUE-5197 [assist] Lazy load the assist tabs
* b9e57c0 HUE-5186 [core] Get rid of deprecation warnings for Moment.js
* 03beba5 HUE-5199 [editor] No blue highlighting of single line query when doing multi queries
* ce1eadd HUE-2753 [search] Nested text facet should propose the 'show more' option
* cb296dc HUE-5189 [core] Add Hbase to Assist
* e659bcf HUE-5196 [metadata] You can't search for the same query multiple times
* a412c42 HUE-5195 [metadata] Nav autocomplete should have shadow like the other drop-downs
* e35b11c HUE-5194 [assist] Collapse button is hidden behind nav search when there are no tabs
* 0b391fd HUE-5192 [assist] Add show details to right-click context menu
* 087179d HUE-5193 [assist] Don't show an error in case the collection size is zero
* e9f438b HUE-5191 [useradmin] Paginate the list of results
* 023e232 HUE-5188 [notebook] Add assist JS imports to the main page
* fbbe2e0 HUE-5185 [beeswax] Remove dependency on VKBeautify
* 8b79e20 HUE-5167 [core] Improve SASL error reporting in HUE
* 05adc61 HUE-4888 [fb] Display S3 region to avoid misunderstandings
* acdc035 HUE-5184 [indexer] Do not error when listing collections on non Solr Cloud mode
* 5f95b66 HUE-5182 [core] Centralize assist JS models imports
* caa995f HUE-5180 [search] Use pushState to change URL when saving a new collection
* 318e233 HUE-5181 [editor] Clear editor selected query on SQL file drop from desktop
* 7c32b80 HUE-5145 [metadata] Add Similar Query API
* f7bb58a HUE-2173 [search] Support nested text facet with &up
* 34b3ab2 HUE-2173 [search] Apply sort on value of function when using an aggregate
* 95412b3 HUE-2173 [search] Apply proper ascending or descending sort
* ef4eeed HUE-5145 [metadata] Integrate APIs into the editor
* 02d7cf4 HUE-5145 [metastore] Cleaner top favorite tables of a database
* 757324b HUE-2173 [search] Add range to nested text facet
* 0adee37 HUE-2173 [search] Add nested text facet on a string field
* 30e5b0e HUE-4993 [assist] Use ko bindings for the query builder context menu
* 81d3c2f HUE-4993 [assist] Replace double-click to insert with right-click context menu
* e5cc8d8 HUE-5084 [core] Add indexes as Assist Panel
* 76b602b HUE-5178 [core] Fix assist S3 refresh cache
* 42f696c HUE-5069 Create new deployment dir when imported doc points deleted one
* 99b2921 HUE-5069 [core] Running imported workflow fails across users
* 03b6c50 HUE-4906 [home] Allow superuser to trash shared documents
* 4de01d3 HUE-5177 [home] Operation menu does not fit well on page with a top banner
* 502fc2e HUE-5166 [impala] Handle empty session properties during upgrades
* 2581664 HUE-5172 [core] Update FontAwesome to 4.7
* 9e1171a HUE-5168 [indexer] Smaller input size for file types
* d77881f HUE-5168 [indexer] Populate default collection name automatically
* 7d0450a HUE-5168 [indexer] Polish interface by hiding non essential fields
* 627d496 HUE-2173 [search] Nested tree widget with functions
* 9b883da HUE-2173 [search] Nested tree widget with dimension 2
* eec86f3 HUE-2173 [search] Nested tree widget with dimension 1
* b75d88f HUE-3281 [home] Add link to Job Browser 2 to the menu
* d1875c7 HUE-5145 [editor] Update top tables query to take  database in parameter
* 3ca8d78 HUE-5145 [editor] Skeleton of statement compatibility API
* 439361d HUE-5145 [editor] Skeleton of query risk API
* a1729b3 HUE-5145 [metadata] Add skeleton of table_details API
* b6eb1d1 HUE-2173 [indexer] Do not require Solr Cloud mode to get displayed
* 27a2907 HUE-3281 [core] Adding link to more snippets in meu if admin
* 2e943aa HUE-3281 [core] Add more icons for the main editors
* 2e5cc66 HUE-3281 [home] Refacor the top menu to simplify its UX
* 9fa2256 HUE-3281 [home] Add list of interpreters in the compose menu
* f28b3c7 HUE-3281 [home] Disable dynamic loading of component until it is ported out of require
* fd41c0b HUE-3281 [core] Rebase to start the new layout
* da5ba55 HUE-3281 [core] Use ko components for editor and metastore
* 009c61d HUE-3281 [core] Add the assist panel
* 2797d67 HUE-3281 [core] Add basic menu content
* 0f29889 HUE-3281 [core] Fix left nav and page width issues
* ac48b2d HUE-3281 [core] Add left menu
* 633b66d HUE-3281 [core] Use flex layout for top bar and page contents
* 4242f65 HUE-3281 [core] Add top nav
* a60cdc1 HUE-3281 [core] Responsive skeleton
* 1c092f8 HUE-4993 [assist] Assist entry optimization
* 8f8ad7e HUE-4179 [metastore] Use common selected DB for hive and impala
* 60d0a03 HUE-5171 [assist] Remember the last opened panel
* 1e390c7 HUE-5164 [editor] Result grid should give hints on hover
* 4ed34b2 HUE-5157 [editor] Add asterisk locations and expansion back to the editor
* 82727a1 HUE-5159 [editor] Fix broken jasmine tests for HDFS locations
* aa8eda0 HUE-5163 [security] Speed up initial page rendering
* f135f6d HUE-5154 [oozie] Create an new oozie workflow throws server error 500
* fc8055a HUE-5145 [metadata] Remove old data mock option
* 36f9b25 HUE-5162 [oozie] Add tests on creation of new workflow, coordinator and bundle
* 06b82cb HUE-5125 [editor] Show file tree on context popup
* fbbb534 HUE-5151 [editor] No result in Query History search in editor toggles to Saved Query tab in FF
* fc58e04 HUE-5161 [security] Speed up roles rendering
* 7a53e78 HUE-5158 [editor] Fix database name case issue in autocompleter
* d7d8b50 HUE-5156 [editor] Fix issue where search is active after clear and switching tabs
* 93adbb5 HUE-5155 [editor] Make nav autocomplete icons bigger
* 5443601 HUE-5160 [search] Avoid JS error on missing field check
* 2e50b41 HUE-5149 [metadata] Support tags:hue syntax in result view
* 938bd3c HUE-5149 [metadata] Add highlighting to the result records
* c9298b6 HUE-5149 [metadata] Print description of object in result
* 7869628 HUE-5149 [metadata] Avoid error on list_tags
* ab5e0bb HUE-5149 [metadata] Only highlight in the name of the object
* dcc226d HUE-3281 [core] Assist for small screens
* 5b0d9e8 HUE-5150 [metadata] Don't do nav search on empty input
* a4e7b59 HUE-5149 [metadata] Mark autocomplete matches in bold and not italic
* 1b377d0 HUE-5135 [metadata] Add syntax highlighting with <em>
* 2199bcd HUE-5135 [metadata] Autocomplete highlighting on matching terms
* b307b78 HUE-5135 [metadata] Add proper autocomplete highlighting to matching facets
* 47c8a8a HUE-5145 [metadata] Basic of upload optimization API
* 38895a4 HUE-5145 [metadata] Rename API tests to client tests
* 943a75a HUE-5145 [metadata] Get top tables from optimization API
* 4d77d46 HUE-5145 [metadata] Get tenant from optimization API
* be5216f HUE-5148 [metadata] Show message when no autocomplete result is found for nav search
* 8f9c38f HUE-5147 [metadata] Add counts to nav search autocomplete results
* f67a3c5 HUE-4958 [home] Don't try to open single file in home automatically
* 94ef74b HUE-5105 [jb] Opening an "ACCEPTED" job can return 500 error
* 263b9a4 HUE-5140 [impala] Failed to get query profile from Impala Daemon server
* 5060af5 HUE-5146 [editor] Add ctrl+space shortcut description to the editor help
* e0e7567 HUE-5126 [fb] Filechooser can have some autocomplete error
* 255568a HUE-5135 [metadata] Do not send * query when typing a second term
* c875f7a HUE-5143 [jb] rm_ha decorator decorator does not specify the user correctly
* e05cb3e HUE-5135 [metadata] Keep default filtering on list of allowed types by source
* efec570 HUE-5144 [metadata] Tune the timings of the context popover for Nav search results
* d9c5db8 HUE-5142 [metadata] Don't save tags when they haven't changed
* 8f985ad HUE-5122 [fb] Enable back execute bit permission set for HDFS files
* bd026a6 HUE-5135 [metadata] Case insensitive facet value matching
* d79b29e HUE-5135 [metadata] Make sure type value still makes sense for the source
* 517a59a HUE-5135 [metadata] Case sentitive type: search and allow custom values like FIEL*
* 314bfd9 HUE-5028 [oozie] User can't edit shared WF with modify permissions in new editor mode
* d3cf3f7 HUE-4897 [core] Import document call should provide information about the import
* 6b20d8a HUE-5137 [editor] Fix save query JS error
* 14bf3a7 HUE-5123 [notebook] Creation of notebook snippet with shell action
* 997158a HUE-5121 [home] Old query format with / cannot be imported
* 9b9eafd HUE-5139 [metadata] Delete search words on ctrl + backspace
* 9711cae HUE-5138 [metadata] Fix funky positioning of context popover in the search results
* 98cc47b HUE-5125 [editor] Skeleton for HDFS details in context popover
* e06e6ae HUE-5136 [editor] Fix JS console error for token.value
* cf9a200 HUE-5134 [editor] Fix incorrect UDF locations for analytic functions
* 4d9a68c HUE-5133 [metadata] Show search result on enter
* 666b4df HUE-5135 [metadata] Prevent CSRF error when calling the search API
* 12821d5 HUE-3281 [search] Mobilified collection list and dashboard
* 91c7efe HUE-5127 [core] Revert typo about Python 2.6 in Makefile
* eb586e4 HUE-5130 [jobsub] Allow Sqoop 1 job even if Sqoop 2 app is not available
* 9932445 HUe-5119 [oozie] Define statements for Hive snippets of notebooks
* fc1e7cd HUE-5097 [core] Add argparse for the sqlformater compatibility with Python 2.6
* 99a14be HUE-5120 [core] Also log the potential detail of the PopUpException
* 5c327f2 HUE-5127 [jb] Link text labels to its radio button
* 4f9c93f HUE-5127 [jb] Remove coordinator actions from the editor
* 7037387 HUE-3281 [editor] Disable swipe to slide
* c41ede7 HUE-3281 [editor] Enabled results
* 6f2e7b1 HUE-5127 [jb] Integrate coordinator actions in revamp
* 63bfbfa HUE-5119 [oozie] Offer file output path to Hive query batch
* e466707 HUE-3281 [editor] Added jquery touch swipe
* d7d1038 HUE-3281 [editor] Modified mobile skeleton
* ee9b040 HUE-3281 [editor] Simplified mobile version skeleton
* 05f914d HUE-5120 [core] Popup Exception should log the original stack trace
* 1824832 HUE-5119 [oozie] Email result on batch completion
* 73d3edc HUE-2173 [search] Remove new line on editing mode
* 7f42afa HUE-2173 [search] Add readonly dimension switch
* 57a7bc8 HUE-2173 [search] Support global timeline filter
* 3fbb7f4 HUE-2173 [search] Have pie and bucket widgets use the same dimension snippet
* 0c75a92 HUE-2173 [search] Refactoring to share the dimension display in common
* 054afea HUE-2173 [search] Skeleton of Analytic gradient map widget
* 653444e HUE-2173 [search] Remove duplicate dimension add to widget
* fe082df HUE-3281 Interface revamp and modernization of UX: Hue 4
* cbf166e HUE-2173 [search] Skeleton of Analytic timeline widget
* 82516e9 HUE-2173 [search] Automatically choose the field if there's just one field available
* 7b28677 HUE-2173 [search] Fix pre-population of the field chooser
* 89da56f HUE-2173 [search] Fix top margin
* 5ba3152 HUE-2173 [search] Make it responsive
* a64718a HUE-2173 [search] Introduce the Analytic Pie chart
* 6bcc748 HUE-5127 [jb] Add loading job property
* 90d8cbd HUE-5127 [core] Added basictable for responsive tables
* 316332a HUE-5127 [jb] Integrated coordinator actions on detail page
* b003d24 HUE-5127 [jb] Added assist to JB
* 8a8cf24 HUE-5127 [jb] Added hashchange to the apps page
* 6e49c81 HUE-5127 [jb] Added observableDefault to KO
* 6d88fc4 HUE-4873 [security] Change login modal UX
* 16dd0a7 HUE-4873 [security] Deliver csrftoken cookie with "HTTP_ONLY" bit set when HTTPS
* 9bbc09f HUE-4653 [core] Build a HTTP Client pool
* 1c06e78 HUE-5076 [core] Unpack thrift handle guid, secret before adding to logs
* 57748b1 HUE-5067 [oozie] Graph display of single executed action shows the full workflow
* 0c66cc9 HUE-5097 [editor] Plugin the new SQL formatter in the editor
* 313e92c HUE-5097 [editor] Introduce sqlparse lib for formatting and splitting SQL statements
* 6d6982c HUE-5188 [editor] Add heatmap functionality to the leaflet map chart
* 37ae3cd HUE-5109 [oozie] Update test to take into account the email content-type
* 89fb005 HUE-5112 [oozie] Protect against invalid parameter values in document action
* 086b276 HUE-5109 [oozie] Allow sending of email report when submitting a workflow
* 56f0701 HUE-5108 [oozie] Workflow dashboard page with an email on kill or end has a js error
* 608fbf2 HUE-5110 [oozie] First workflow save starts blinking the 'unsaved' feature in the editor
* d55eb79 HUE-5111 [oozie] Add margin to the last widget on the workflow editor
* 20f5e78 HUE-3984 [jb] Failed MR application cannot be found even if still in RM
* cba68a0 HUE-3079 [jb] Display jobs from JHS (YARN and Spark) and their logs when not in RM
* 9c02273 HUE-5107 [oozie] Restyle document autocomplete to look more like a dropdown
* c4690b9 HUE-4826 [fb] Allow to edit the path in the file chooser
* b5b46b9 HUE-5083 [charts] Improve redistribution of labels on bar charts
* 19f29d9 HUE-5090 [oozie] Refactor batch API submittion of a Notebook
* bbd710e HUE-5090 [oozie] Initial prefixing of Oozie scheduled jobs
* eb12788 HUE-5090 [oozie] Initial prefixing of Oozie batch jobs
* bc5e14d HUE-5090 [editor] Rename correctly options for exporting data into a file
* d760de1 HUE-5090 [notebook] Refactor creation of a notebook with Hive or MR snippets
* 1b2daef HUE-5103 [core] Add little blue footer to login page
* 6379b3f HUE-4991 [oozie] Group Coordinator dashboard action buttons
* c4120a4 HUE-5098 [oozie] Swap readonly Codemirror to Ace
* b3a3aea HUE-5099 [editor] Avoid scrolling to top of the editor when executing a statement
* 48d915d HUE-5093 [metadata] Use correct logic to check for app permission
* 467633e HUE-5095 [backend] Python requests library should put port information in log message
* e99a6e0 HUE-5093 [metadata] Support partial facet matches in autocomplete
* 90af786 HUE-5093 [metadata] Sort facet values by counts
* 47c2064 HUE-5093 [metadata] Allow the listing of non default types in the autocomplete
* 1099ebc HUE-5093 [metadata] Initial show sample popup on hover in search result
* 095fbb7 HUE-5093 [metadata] Add counts to facet listing
* 4ddd211 HUE-5093 [metadata] Have tests use an augmented user like after a real login
* 8fd2a75 HUE-5093 [metadata] Show context popover for tables and fields in the navigator search results
* ca28774 HUE-5085 [editor] Fix context popover for backticked identifiers
* 09c22b7 HUE-5077 [metadata] Prefix filter and keep the potential facets
* 37d3df9 HUE-5092 [editor] Column search just by type or name
* 7578aec HUE-5091 [charts] Stabilize map chart
* 3cfb2c4 HUE-5081 [home] Unify import JSON modals
* e8f7494 HUE-5086 [metastore] Fix create table JS error
* 1c01549 HUE-5050 [core] Logout fails for local login when multiple backends are used
* 4f2c76a HUE-4181 [hive] Parse Hive MR query row count and size from job counter data
* 5de3f14 HUE-4969 [core] fixing Support hive.server2.thrift.sasl.qop="auth-conf"
* 874d728 PR436 [hive] Multiple Hive sessions for Tez
* 0625ad0 HUE-5078 [core] Omit irrelevant files and paths in coverage
* e6f1e2f HUE-4886 [impala] Fix live cluster tests for impala row count
* cf0b845 HUE-5077 [metadata] Provide more facets
* 4a7dc796  HUE-5074 [chart] Timeline tooltip can make the graph flicker
* d946027 HUE-5082 [metadata] Add more facets to nav search
* 4d1e075 HUE-5080 [editor] Fix JS error for SQL syntax error checker
* 9836d44 HUE-5066 [editor] Move cursor between () when autocompleting a udf
* cdcd130 HUE-5079 [metadata] Show tag edit icon on hover
* a3b6090 HUE-5065 [oozie] Document select for a d&d could guide the user more
* 41c24be HUE-5070 [oozie] Disable start import button until a file is selected
* f321ea9 HUE-5061 [editor] Default alignment does not show the end of column input box and the clearable
* 59a32fa HUE-5075 [core] Call get_absolute_url() only when document content object has the attribute
* 11e0af5 HUE-4957 [metastore] Creating table from file can 500 on the delimiter page
* 9ad5819 HUE-4886 [impala] Parse unabbreviated count for Impala returned rows
* cea2c58 HUE-5057 [metadata] Skeleton to have tags in read only mode
* b806127 HUE-5064 [metadata] Reopen the Navigator search autocomplete when facets are selected
* e0dccf5 HUE-5063 [metadata] Save tags when clicking outside the tag editor in edit mode
* f976ce3 HUE-5062 [metadata] Improve design of Navigator search results
* c4de3f9 HUE-5059 [metadata] Show Navigator search autocomplete on focus
* 4d5b4a4 HUE-5057 [metadata] Add read-only option to the Navigator tag editor
* 0bda037 HUE-4961 [editor] Bar/Line chart rendering issue when user tries toggling Columns icon
* 38430bd HUE-5060 [editor] Chart X axis value is not selectable at times
* 2f28242 HUE-5061 [editor] Default alignment does not show the end of column input box and the clearable
* 1e991c6 HUE-5049 [editor] Introduce the timeline bar/line chart
* cbd4060 HUE-5058 [metastore] Skip test_read_partitions unless in live cluster mode
* 7b5ac49 HUE-4886 [impala] Get resultset row count
* ed6f84d HUE-5057 [medata] Only show enrichment if the user has the permission
* 63c57d8 HUE-4996 [editor] Nested types can not be extended in assist
* f08b421 HUE-5015 [core] Install examples get "column username is not unique" if "hue" user exists
* 8cdc2aa HUE-4838 [editor] Add S3 browsing to the assist panel
* 449b2f5 HUE-5056 [editor] Delay history and saved query search to when the user stop typing
* f9e3524 HUE-5051 [metadata] Remove empty facet values
* 4dc99b7 HUE-5051 [metadata] Remove empty filters like 'tag:*'
* c8757da HUE-5051 [metadata] Add default source filters to autocomplete
* 439a524 HUE-5051 [metadata] Facet autocomplete should apply previous query filters
* 2156255 HUE-5055 [editor] The chart multiple Y columns are not always loaded back on page refresh
* 59afb57 HUE-5054 [editor] MapChart binding is called at saved query page refresh
* a1e653c HUE-4839 [editor] Add my documents to the assist panel
* e32b11f HUE-5053 [home] Fix search icon overlap
* 42e0662 HUE-5052 [home] Rename file browser to doc browser
* b92f8d4 HUE-5048 [frontend] Remove RequireJS dependencies
* 0f04045 HUE-5048 [frontend] Remove RequireJS from jasmine tests
* a6bdead HUE-5048 [frontend] Remove RequireJS from home and wizards
* e540078 HUE-5048 [frontend] Remove RequireJS from the metastore
* f63e55d HUE-5048 [frontend] Remove RequireJS from the editor
* 852c196 HUE-4388 [editor] Fix unit test TestDocument2.test_get_document
* 098920e PR437 [fb] Use relative URLs to support gateway/reverse proxy
* a8e0df8 HUE-5040 [notebook] Keep the progress bar to 99% orange until the status of query is READY
* fe99a2e HUE-4987 [oozie] 500 error when listing bundles
* 106cb30 HUE-5045 [core] Avoid showing jHueNotify messages if the content is empty
* b79e8ae HUE-3276 [assist] Load more HDFS entries on scroll to the end
* 99061a3 HUE-5043 [core] Fix wrongly closed html and svg elements
* b51a7eb HUE-4680 [editor] Horizontal scroll on SQL result with touchpad very slow on FF
* 6fad03e HUE-4995 [oozie] Provide Email notification option at workflow submission
* 58edfc7 HUE-5026 [core] Warn in logs on startup if ldap_url contains "ldaps://" and use_start_tls = true
* 13f09cd HUE-5041 [editor] Hue export large file to HDFS doesn't work on non-default database.
* 3313039 HUE-5000 [metastore] ALTER database properties API
* f3090ca HUE-4672 [metastore] Gracefully fail if the input file is invalid for an external table
* 51bc876 HUE-5039 [charts] Remove &nbsp; from the scatter chart legend
* dcb17f3 HUE-5035 [charts] Avoid double bar chart rendering on window resize
* 992ef98 HUE-5038 [assist] Use the active assist tab for nav search
* 50bf71c HUE-5037 [assist] Increase spacing between the action icons
* c72a8b1 HUE-5036 [editor] Improve tag editor UX
* dac2722 HUE-5032 [editor] Improve navigator search facet matching
* 489af81 HUE-5033 [editor] Preselect Y-axis going back and forth of pivot bar charts
* 636600f HUE-5031 [charts] Pivot bar chart colors should stay the same for the series
* 20d1619 HUE-5029 [charts] Remove &nbsp; from multiBar legend
* dd56ea0 HUE-4388 [editor] Warn when deleting document with dependents
* d77d9e8 HUE-4999 [impala] Set default Impala idle_session_timeout to 1 hour
* 32b764f HUE-4997 [impala] get_partitions is not being closed
* 2cd56f6 HUE-5024 [editor] Exporting results to HDFS or new table changes the editor type from Hive to SQL
* 6c4d044 HUE-4998 [impala] get_configuration is not being closed
* 1531376 HUE-5014 [core] Prevent copying a Document folder into itself which then creates a recursive depth issue
* 83742c9 HUE-5009 [core] Make ignore unicode decode errors compatible with Python 2.6
* d0aacf6 HUE-5020 [editor] Improved facet and multi-word autocompletion in nav search
* 4627a3b HUE-5019 [editor] Load pivot chart preferences on saved queries
* 37f0b64 HUE-5013 [oozie] Avoid splitting draggable actions in two lines
* 35d8638 HUE-5016 [charts] Skip negative values on Pie charts
* b445746 HUE-4012 [charts] Graph 3rd dimension in stacked bar charts
* b4531d8 HUE-5018 [editor] Fix context popover flex for IE
* 33e4043 HUE-5017 [assist] Improve the nav search styling
* 20867d9 HUE-5011 [editor] Use pure CSS instead of KO binding to fix empty assist popover
* 64e31b7 HUE-4931 [fb] Fix parquet decoding error on debug log messages
* 509bef5 HUE-5009 [core] Fix parquet-python version checking to be 2.6 compatible
* 0f2fde4 HUE-5009 [core] Backport parquet-python Fix issues invoking struct methods. (#42)
* 9ff637d HUE-5009 [core] Backport parquet-python Add support for converted_types to dict-encoding.
* 8f73e6c HUE-5009 [core] Backport parquet-python Add support for nulls in PLAIN_DICTIONARY pages.
* f15a44b HUE-5009 [core] Backport parquet-python Fix converted types for plain encoding.
* e895374 HUE-5009 [core] Backport parquet-python Fixes errors reported by flake8 and pylint
* 9cc9b8c HUE-5009 [core] Backport parquet-python Logs error when a fileobj isn't in binary mode
* b3f6c2b HUE-5012 [assist] Switch inner search to filter
* 9713b2f HUE-5010 [oozie] Automatically refresh workflow parameters in a coordinator
* 900b8f9 HUE-3666 [core] Autocomplete plugin to select and filter from all the documents
* 0e55a51 HUE-5011 [editor] Fix empty context popover in Safari
* f560e67 HUE-4082 [assist] Fix issue with blank assist
* 6c2eeb6 HUE-5006 [assist] Only show the active filter in the editor
* 7eb51f4 HUE-4986 [oozie] Allow parameters in workflow name
* da52675 HUE-4943 [fb] Error trace when trying to download files that are missing perms
* d978e80 HUE-4954 [editor] Add variable attribute in default snippets of notebook
* 948caa6 HUE-4954 [oozie] Prevent js error when schedule model is not completely loaded
* 9f59cff HUE-5007 [core] Get ride of bad utf8 character when doing make-locale
* 5926dd2 HUE-5007 [core] Update localization for de, es, fr, ja, ko, zh
* 7fe7172 HUE-4989 [oozie] Automatically get and set the SSL truststore path from ssl-client
* de007e2 HUE-4989 [oozie] Pickup SSL truststore path from ssl-client.xml
* 3eab32f HUE-4979 [editor] Add column count on the context popover
* 48d59cd HUE-4868 [oozie] S3 workflows links are wrong in the dashboard
* d196180 HUE-5001 [metastore] Improve the positioning of DB tags
* 89f879a HUE-4954 [oozie] Be explicit when schedule changes need to be saved before starting
* 28e3c0e HUE-4954 [editor] Refresh schedule parameters on save
* 0c67608 HUE-4954 [oozie] Automatically pick up the variables from the notebook
* 486f85b HUE-4954 [oozie] List workflow dashboard coming from a coordinator pointing to a document
* d140821 HUE-4954 [editor] Generate and submit the coordinator
* 13f4e03 HUE-4954 [editor] Edit and save the coordinator
* fa9f923 HUE-4954 [editor] Load and save the managed coordinator
* 7d63129 HUE-4954 [editor] Indent saving info requirement
* 454a554 HUE-4917 [fb] S3 upload progress of large files is not consistent
* 93267e7 HUE-4962 [editor] Sample popup should save its last size
* 982d7cb HUE-5005 [assist] Add filter for showing only active editor tables
* 8b558b9 HUE-5002 [editor] Improve nav tag edit mode layout
* 8a8ba49 HUE-5003 [core] Prevent JS error on calling scroll to column on just initialized HueDataTables
* f033cc6 HUE-5004 [editor] i18n missing on popover titles
* 85b9ab0 HUE-4994 [oozie] Consider default path for decision nodes in dashboard graph
* 63427b6 HUE-4982 [editor] Initial styling of the nav autocomplete
* 39aadcf HUE-4985 [editor] Query builder fix in new editor
* 1467d54 HUE-4878 [editor] Click to select a row in query result grid is gone
* 02d36c9 HUE-4988 [metastore] Fix js error related to tagging
* 7c3683a HUE-4982 [editor] Use the nav api endpoint for search autocomplete
* c4a1e16 HUE-4953 [core] Scrolling past 100 records on the table hides the top left cell of the fixed header
* 83a3b46 HUE-4983 [notebook] Notebook pages can list objects on two rows
* d231c3b HUE-4942 [metadata] Default set of objects for each panel of assist
* d89324f HUE-4982 [editor] Add skeleton for nav search autocomplete
* 4b16a63 HUE-4830 [editor] Autocomplete shouldn't suggest SORT BY after ORDER BY
* be0f01b HUE-4981 [editor] Add SQL parser support for NOT in front of RLIKE and REGEXP
* b2fc59f HUE-4979 [editor] Fix the context popover metastore and assist links
* fad5e60 HUE-4975 [fb] Keep end of breadcrumbs visible with longer paths
* 57694f8 HUE-4980 [editor] Format queries with AS keyword fails
* 126a764 HUE-4949 [editor] Add LIMIT 100 to drag & drop table from assist
* c94f144 HUE-4942 [metadata] Support custom end user filters
* e23c0b6 HUE-4978 [editor] Make the parser aware of database locations
* ae8bc5b HUE-4977 [metastore] Promote querying the table in the editor
* b141170 HUE-4892 [editor] Support CTRL+enter in parameter inputs
* ed5f502 HUE-4974 [editor] Use the new tag component in the metastore
* fe99bc7 HUE-4970 [editor] Editor does not horizontally scroll on autocomplete with <enter>
* 094d428 HUE-4971 [metadata] Support query filters as search terms
* be05dc8 HUE-4685 [editor] Loading a query has a big gutter which is smaller when you click it
* 7b79f85 HUE-4817 [fb] Filter box in filechooser picker
* a1083f0 HUE-4968 [oozie] Remove access to /oozie/import_wokflow when v2 is enabled
* 85da54d HUE-4811 [oozie] Remove link to sub-workflow dashboard from editor
* 146c408 HUE-4966 [metadata] Tweak search result display a bit
* 7e63d69 HUE-4966 [metadata] Removing spinning forever on search
* c584706 HUE-4966 [metadata] Introduce interactive facet API for autocomplete
* 3545f02 HUE-4967 [editor] Add edit mode for navigator tags
* 81c97be HUE-4845 [fb] Filechooser picker is not getting escape key
* d3d820b HUE-4964 [editor] Make it possible to edit tags in the context-popover
* 68deb7d HUE-4879 [editor] Column sort does not filter out NULL
* 1a12d53 HUE-4828 [fb] Reset search filter when opening a directory
* d1539b5 HUE-4905 [editor] Result filter bar does not have any blue on hover effect
* 18cce08 HUE-4956 [metadata] Filter metadata not on the same cluster
* f934788 HUE-4955 [editor] Show navigator tags in the context-popover
* 22b699b HUE-4813 [core] Disable collecting referrer URL in Google Analytics
* be851c5 HUE-4887 [editor] Query history syntax highlighter does not handle Chinese char properly
* 8c2f72a HUE-4876 [assist] Drag & Drop a table to the editor broken with FF
* 6199813 HUE-4711 [impala] Error highlighting does not work with multiquery
* fa3264a HUE-4855 [notebook] Dynamically display if a query or notebook can be batched or scheduled
* c1d11ab HUE-4855 [notebook] Get a consistent notebook based on how the editor is open
* fb340ed HUE-4855 [notebook] Notebook or editor gets the list of all available snippets
* 256e573 HUE-4855 [notebook] Offer batch submission only when all the snippets support it
* 34139ca HUE-4952 [core] Top menu disappears completely below 800px
* 4efcb8d HUE-4951 [assist] Scroll to column data in sample popup can be incorrect
* 4f073c2 HUE-4890 [editor] Graph bars are not in the same order as the column legend
* 990d721 HUE-4862 [editor] Add support for qualified identifiers to the context-aware popup
* 593f134 HUE-4914 [assist] Remove odd scroll bar on column list of a table
* ed732f8 HUE-4946 [core] Remove source mapping from JS plugin files
* db47398 HUE-4942 [metadata] Proof that we can have a different search by assist
* 978df98 HUE-4942 [metadata] Display views properly and limit results to 25 to speed up
* ba035ab HUE-4942 [metadata] Update logic of to make the search input really clearable
* 71ee364 HUE-4942 [metadata] Restrict search by default to tables and views only
* 4a745cd HUE-4940 [editor] See which charts are used the most
* 7b70fce HUE-4941 [editor] fixed Content Security Policy directive blocks an image when navigating on marker map
* 5c7f7ca HUE-4937 [core] Set audit_event_log_dir and audit_max_log_file_size config values from Navigator conf if found
* 2b0f991 HUE-4938 [editor] Fix issue where the map crashes the browser for large coordinate values
* 0019319 HUE-4921 [oozie] Workflow dashboard page should not fail when properties have unicode characters
* 6e91f19 HUE-4935 [aws] Enable support for AWS security token
* 81472af HUE-4932 [metadata] Adding several test to list_tags and suggest
* a1bcf4d HUE-4932 [metadata] Adding API to suggest
* dd34d2d HUE-4932 [metadata] Add list_tags to the metadata API
* 6ebfa46 HUE-4933 [editor] Fix issue with missing sample in pinned context
* da9579a HUE-4912 [editor] Add fixed first column to samples in context-popover
* 13fec9e HUE-4930 [core] Fix clearing cookie option in HttpClient
* 1248c19 HUE-4916 [core] Truncate last name to 30 chars on ldap import
* a74bf7e HUE-4928 [oozie] New Spark action can't be added in workflows
* 2e10e7e HUE-4910 [editor] Fix issue where headers become scrambled after viewing the graph
* 41b4fdb HUE-4910 [editor] Fix header positioning for the samples table in the new context popover
* 2a2ffa0 HUE-4910 [editor] Fix header issues when selecting columns
* 98a388d HUE-4726 [core] Default buffered file stream to 128 MB chunks
* 858bbf8 HUE-4726 [fb] Add test and sample file to read parquet snappy file
* 26866c5 HUE-4726 [core] Fix struct.unpack error for Python 2.6
* d6437f9 HUE-4726 [core] Display exceptions in logs when reading file formats
* 8690c1a HUE-4726 [core] Import OrderedDict from compatible module for Python 2.6
* 1d414c3 HUE-4726 [core] Update parquet-python to use Python 2.6 compatible dict comprehension
* b4aac26 HUE-4726 [core] Upgrade parquet-python to 1.1 and include dependencies and backports
* 4bc6b89 HUE-4898 [core] Exporting documents should generate a filename with date and num docs
* cfe4934 HUE-4910 [editor] Use the new table extender plugin for samples in the context pop-over
* eebb265 HUE-4910 [editor] Improved performance of fixed result headers
* b52bb14 HUE-4885 [editor] Silently hide the known non support operations from erroring out
* 2bfe4f7 HUE-4761 [spark] Little clean-up on indentation and logging warnings info
* f99483e HUE-4761 [spark] Make sure dict properties values are proper List types
* 14c7d0b HUE-4871 [useradmin] an unprivileged user can enumerate users
* da45f7e HUE-4891 [useradmin] an unprivileged user can list document items
* 61e1912 HUE-4910 [editor] Increase performance of fixed result headers
* 0e57b8b HUE-4910 [editor] Fix result header widths and improve Firefox scroll performance
* e82a383 HUE-4904 [editor] Bump name length of saved query
* 13f2cc5 HUE-4885 [editor] Integrate result row count when available
* 7081ed8 HUE-4896 [home] Add deletion confirmation on the home page
* 4bce992 HUE-4815 [editor] Properly handle unicode characters in log output
* dc22578 HUE-4884 [editor] Make the context-popover pinnable
* ffdae14 HUE-4833 [editor] Adjust context-popover position when close to window limits
* 0ec3494 HUE-4833 [editor] Drop the old table stats popover
* 2bbf758 HUE-4833 [editor] Use the new SQL context-popover in assist and metastore
* 537c6c8 HUE-1176 [jb] Add templates to the frontend
* 39296fd HUE-4872 [useradmin] Fixing Hue silently fails auth for ldap backend if "Create LDAP users on login" is false
* d1890bc HUE-4848 [editor] Context popup column search does not filter on column types
* 6c3b9cd HUE-4860 [editor] Update test to have the name of the exported query
* 6a2bdf9 HUE-4834 [editor] Make the context-aware popover resizable
* 3254ace HUE-4875 [editor] Make cancel query more obvious
* 7003811 HUE-4867 [metadata] Clicking on browse table show the generic SQL icon
* fde7f5c HUE-1176 [jb] Split up the APIs in dedicated modules
* 5380a14 HUE-4869 [editor] Fix typo in the name of the spark SQL snippet
* af717fb HUE-4798 [oozie] HDFS FS tip should be updated since we integrated with S3 as well
* e5b6374 HUE-4864 [notebook] Crashes when jobbrowser is blacklisted
* 9b3062d HUE-4860 [editor] Exporting saved query result without a name should use query name
* 9e3260a HUE-4861 [indexer] Fix end to end tests and skip them until the libs are automatically setup
* ad501b5 HUE-4835 [editor] Show partitions in the context-aware popover
* 5fbdee7 HUE-4857 [editor] Columns are not highlighted when there are multiple tables
* bedc719 HUE-4631 [home] DB transaction failing because of atomic block on home page
* 3d777a9 HUE-4057 Fix i18n in delete confirmation popup
* fe5771c HUE-4859 [editor] Add a config flag to enable the extended assist panel and the right context panel
* 115b443 HUE-4837 [editor] Add HDFS browsing to the assist panel
* dcc4f48 HUE-4850 [editor] Fix js error when moving cursor over empty editor
* 927aa37 HUE-4856 [core] Allow beeswax_install_examples to accept optional DB name
* 76cea3e HUE-4853 [metastore] Browse and open in editor are duplicates
* 9b66b98 HUE-4823 [fb] Display exception when Hue is configured with invalid S3 access key
* cdb3144 HUE-4822 [editor] Only run HS2 fetch_result_size tests in live-cluster mode
* 5465bbd HUE-4057 [home] Show list of files in confirmation popup when sending files to the trash
* d55627c HUE-4824 [fb] Return graceful error message on failure to open a certain bucket
* fdebc1b HUE-4846 [editor] Export to a file should provide a default name
* 78f6562 HUE-4825 [fb] Filechooser view should return buckets in alphabetical order
* 6c4c214 HUE-4827 [fb] Pointing to a wrong S3 region breaks with no information
* 48a8b61 HUE-4822 [editor] Provide live-cluster test harness for HS2 editor tests
* 8d01584 PR-424 [search] Correct check for undefined variable
* 4a05026 HUE-2854 [metastore] Delete databases with tables
* b0fec96 HUE-4035 [editor] Add column search to context popover
* d177852 HUE-4832 [editor] Show tooltip when hovering over context popover tokens
* c6ed6da HUE-3226 [oozie] Allow to Drag & Dropped a saved MapReduce job into a workflow
* 08e8e73 HUE-3226 [connector] MR snippet
* 0bec844 HUE-4750 [oozie] Drag & dropped a saved Shell query
* 6d524fb HUE-4750 [connector] Shell snippet
* de230fb HUE-4814 [oozie] XML escape variable names in editor submissions
* 0185665 HUE-4809 [hive] Add trustore parameters only if SSL is turned on
* 4d6e893 HUE-4821 [oozie] Support arguments in Hive2 workflow action
* ea3813e HUE-4816 [oozie] Execute from Filebrowser fails with execute permission
* 75ac0b6 HUE-4831 [editor] Refactor HS2 tests with Hadoop
* 81b57d0 HUE-4810 [core] Fix tests by setting data to valid JSON type
* cfbd74d HUE-4785 [editor] Favour continuous partial matches in the autocomplete results
* 37458d3 HUE-4789 [editor] Add autocompletion of values when the cursor is inside quoted values
* 0e9e25e HUE-1176 [jb] Load info of single job when selecting it from the list
* 04413de HUE-4797 [oozie] Drag & Drop a DistCp script as an action
* aac4a0d HUE-4797 [connector] DistCp snippet
* 9ef4bb7 HUE-4809 [oozie] Only add trustore paths when they are actually existing
* 0662519 HUE-4801 [oozie] When importing oozie documents and remapping UUIDs, data should be updated accordingly
* 1994066 HUE-4814 [oozie] fixing oozie job submitter should escape XML params
* 8c468a5 Removed Ctrl-E keybinding (editor.create.new) on macOS (#420)
* bcdfc28 HUE-2689 [oozie] Sub-workflow submitted from coordinator gets parent workflow graph
* 05d157e HUE-4808 [oozie] Don't show the edit link for sub workflows when submitted outside Hue
* 91a8e76 HUE-4703 [yarn] fixing alternatively Correct username is not used on hard failover
* b93b883 HUE-4035 [editor] Introduce the details tab in the smart context popover
* 34da3e3 HUE-4805 [search] HTML widget preview update does not happen automatically
* 0c683c4 HUE-4804 [search] Download function of HTML widget breaks the display
* 576b861 HUE-4801 [core] Do not hide the username in small resolutions
* 7e2d25f HUE-1176 [jb] Adding Batches and Schedules based on Oozie
* 99c5e95 HUE-1176 [jb] Skeleton of Revamp v2
* cb8264a HUE-4706 [core] Importing documents should ignore reserved directories (home and trash)
* f7eded5 HUE-4181 [hive] API to provide result set row count and data size
* 4aa411b HUE-4778 [backend] Fixing the utils.http.is_safe_url function in Django does not properly validate URLs
* 90f3063 HUE-4777 [backend] Fixing The utils.html.strip_tags function in Django can cause a denial of service
* d593f7e HUE-4770 [backend] Fixing Avoided creating a session record when loading the session.
* 59861a1 HUE-3878 [oozie] Drag & Dropped a saved Sqoop1 snippet
* 17fb361 HUE-3878 [editor] Sqoop DB import snippet
* 28e53bc HUE-4787 [editor] Fixing Marker map tiles are not showing up
* 75279c2 HUE-4781 [notebook] Fix export to hdfs to use download_cell_limit from beeswax.conf
* 673f795 HUE-4793 [editor] The context-aware popover should show column sample and analysis
* 2c29fa6 HUE-4791 [editor] Add function description to the context popover
* 6b9f823 HUE-4792 [editor] Add autocompleter support for Hive array, binary and map UDFs
* b059cec HUE-4701 [editor] Older saved queries throw "'NoneType' object has no attribute 'update_data'"
* 84b00c4 HUE-4338 [editor] API to provide result set row count and data size
* dde3211 HUE-4032 [editor] Show table sample and analysis for tables in the editor
* b4069b9 HUE-4032 [editor] Only mark the column location in schema qualified references
* 6037913 HUE-4032 [editor] Skeleton for context aware popover
* 803532e HUE-4032 [editor] Check for locations on load
* fcd3a43 HUE-4773 [editor] Autocompleter spins forever when completing subqueries containing asterisk
* 1dc7527 HUE-4771 [editor] Use parser locations for click to open tables in the metastore
* 8d99b90 HUE-4765 [security] Fixing http_client should use SSL_CIPHER_LIST from conf
* 6f6e43f HUE-4769 [editor] The autocompleter should support INSERT OVERWRITE DIRECTORY
* 4015db9 HUE-4768 [editor] Autocomplete is being called multiple times when the cursor is on top of '*' in a select statement
* 4aaa92e HUE-4767 [editor] Limit the autocompleter length before and after the cursor
* d5860da HUE-4766 [core] Replace illegal characters on CSV downloads
* 256a408 Fixing HUE-4703 [yarn] Correct username is not used on hard failover
* 5e46c12 HUE-4738 [oozie] Use Concurrency and Throttle values set in coordinator settings
* 6aa2c00 HUE-4764 [metastore] Show an indication when the partition limit is reached
* 1c368b2 HUE-4763 [editor] Update the editor keyword highlight rules for Hive and Impala
* 5145007 HUE-4319 [editor] Add Impala refresh dialog to assist DB list view
* 23a12a8 HUE-4640 [editor] Fix for DB prefix autcomplete when typing table names after "? FROM db."
* 0654ecf HUE-4760 [core] Fix error with indexer config when search is disabled
* f5e72fd HUE-4759 [editor] Don't suggest tables in the select list when there is a FROM clause
* d553763 HUE-4525 [beeswax] Correctly parse Tez jobs and add functionality to test multiple execution engines
* 8208bb3 HUE-4758 [editor] The autocompleter should suggest keywords at the start of a statement
* 195cd49 PR369 [jdbc] Use CLASSPATH value for creating JavaGateway and load JDBC driver class
* af6d1ef HUE-4755 [doc2] Add is_trashed property to Document2
* d55d1fc HUE-4747 [editor] Improve the UX of download form submission
* 40b40e1 HUE-4754 [editor] Increase default autocompleter API timeout to 5 seconds
* 8d55bae HUE-4753 [editor] The autocompleter doesn't merge columns correctly
* dd83439 HUE-4751 [oozie] Drag & Drop saved Pig script into a workflow
* d5a511f HUE-3224 [connector] Convert Pig connector to offer a new Pig snippet
* 1fa14f6 HUE-4689 [fb] D&D a file into a directory in S3 gets 'RenameFormFormSet' object has no attribute 'data'
* 9e38ad8 HUE-4730 [fb] Notify about failing file upload in file chooser
* 3be53cd HUE-4670 [metastore] Allow headers to be ignored/removed when creating external table
* b44a671 HUE-4747 [editor] Download form should be submitted to a new tab otherwise the snippet gets closed
* fdc395f HUE-4739 [jobbrowser] fixed Jobbrowser tests which were failing after resource manager pool change
* a2b0c25 HUE-4584 [editor] The new autocompleter should support DELETE
* 98c0722 HUE-4734 [editor] Autocompleter should trigger after '.' when autocomplete as you type is enabled
* 704ac40 HUE-4588 [editor] The new autocompleter should support SET
* 06b3d06 HUE-4589 [editor] The new autocompleter should completely support COMPUTE and DROP STATS
* f593861 HUE-4590 [editor] The new autocompleter should support INVALIDATE METADATA
* 8f311f7 HUE-4591 [editor] The new autocompleter should support REFRESH
* 4f19b85 HUE-4732 [editor] Autocomplete should work inside parenthesized value expressions
* 93e3b1f HUE-4733 [editor] Autocompleter doesn't support arithmetic operations in in value list
* 47592a6 HUE-4742 [core] Data sample popup HueDataTable renders weirdly on FF
* 03e85be HUE-4713 [oozie] Properly escape the quotes in the example json fixture
* c98fff1 HUE-4675 [metastore] Assist not loaded and pointing to the source on the create table from a file page
* 296a545 HUE-4633 [notebook] Disable by default Oozie integration until 3.12
* bd23fd0 HUE-4736 [editor] The autocompleter throws JS error
* c2e65f2 HUE-4735 [editor] The autocompleter should also suggest tables with '.' when suggesting columns from multiple tables
* e73356f PR415 [liboauth] Fix several bugs in `get_redirect_uri` method and related calls
* 9abfa7a HUE-4727 [fb] Fix WebHDFS upload tests
* 10e36d7 HUE-4727 [fb] Raise warning if CHECKACCESS is not supported
* bb1e66c HUE-4737 [fb] Creating a bucket errors with [Errno 22] Bad Request
* c282a18 HUE-4737 [core] Manually re-apply HUE-4403
* 9d8d8f9 HUE-4737 [core] Re-apply HUE-2943
* 7c63c63 HUE-4737 [core] Upgrade boto to 2.42.0
* c182527 HUE-4415 [editor] Disable "Save" button in query export unless output is filled
* 6e508da HUE-4344 [fb] Buffer reading parquet file and limit in size
* 49aa1cd HUE-4725 [editor] The autocompleter should handle Impala complex types in the table list
* 931077d HUE-4686 [fb] Bubble up error when trying to create directory in / in filechooser
* b304dd7 HUE-4724 [editor] Closing the table search should un-highlight the selected cell
* 343ede3 HUE-4709 [editor] Search does not load cells when navigating
* 4e94222 HUE-4720 [oozie] Drag & Drop saved Spark app into a workflow
* 1557034 HUE-4706 [core] Importing documents should ignore reserved directories (home and trash)
* 27ad0c1 HUE-4708 [aws] Add test_rename for directory rename in S3
* f3eab39 HUE-4707 [aws] Enable non-US region support for AWS S3
* 61f0c4c HUE-4247 [batch] Support for batch pyspark or spark
* 4a19fc6 HUE-4719 [editor] Search disappears on load of new records
* 97ecc59 HUE-2645 [oozie] More intuitive adding of a PySpark action
* 9101f97 HUE-2645 [oozie] Move Spark option list to the main panel
* ecc87f8 HUE-2645 [oozie] Better Spark action UX
* e8a4147 HUE-4713 [oozie] Spark example should use yarn client mode and show how to add dependencies
* 0a15297 HUE-4688 [editor] Generify references to HDFS when exporting query result to a file
* 1e15595 HUE-4718 [core] jHueScrollUp pollutes the DOM with more than one scroll up anchor
* 825b13c HUE-4683 [editor] Improve tooltip rendering of export results question mark
* 1c2ea32 HUE-4683 [editor] Export result question mark icon does nothing
* 0f414d2 HUE-4705 [editor] Possible XSS when hovering on saved query description
* f6a3f88 HUE-4688 [metastore] Authorize the selection of a directory in the create table from a file wizard
* f4bc5f8 HUE-4704 [security] Fixed Arbitrary host header accepted in Hue
* 32845e1 HUE-4700 [beeswax] Protect against setting XSS in old editor
* 3869ba9 HUE-4699 [editor] Autocompleter fix for decimal values
* a0c5034 HUE-4579 [editor] The new autocompleter should support Impala INSERT statements
* f006dfa HUE-4678 [editor] The label on marker maps is not updated to reflect what you choose on the left side dropdown
* 955280d HUE-4682 [editor] Scroll to a col, reexec the query, the greyed column is still there
* 83ff7e7 HUE-4696 [editor] JS .top error on certain reload/execute combos
* d44e9b7 HUE-4667 [editor] Geo plotting of states is case sensitive
* 29eca42 HUE-4697 [editor] The autocompleter should suggest select list aliases
* b60ffd2 HUE-4665 [editor] Autocompletion of lateral views should not have parenthesis around the column aliases
* d3ee7b7 HUE-4684 [editor] No placeholder showing up in new editors
* 328ebfb HUE-4691 [fb] S3 D&D is allowed after a page refresh but not after opening a directory
* 8637c0d HUE-4676 [editor] Table header is not XSS safe
* 86da957 HUE-4673 [fb] S3 bucket names should automatically lowercase them
* 2958743 HUE-4671 [fb] S3 create bucket should allow underscores in name
* ae8fb4c HUE-4373 [home] Exporting / Importing queries should handle associated workflows and coordinator
* 0f52f8a HUE-4668 [fb] S3 rename directory raises IOError
* f00d088 HUE-4498 [security] Fixed Content Security Policy blocks PDF in HBase app
* bc0dbe7 HUE-4541 [security] fixing Hue job browser - Kerberos mutual authentication error in Hue
* f0793b8 HUE-4666 [search] Use the actual Hue user for impersonating in non secure mode
* ef634ca HUE-4661 [core] Demo backend should keep the admin user logged in
* ff96d1f HUE-4605 [fb] Move and copy in S3 have the HDFS path autocompleters in the popup
* a496a4c HUE-4660 [editor] Ace autocomplete spinner disappears too quick
* a686005 HUE-4659 [editor] Fix an issue with column merging of more than 2 tables
* 665c275 HUE-4662 [security] fixing Hue - Wildcard Certificates not supported


Contributors
------------

This Hue release is made possible thanks to the contribution from:

- Aaron Newton
- Aaron Peddle
- Aaron T. Myers
- Abraham Elmahrek
- Aditya Acharya
- Adrian Yavorskyy
- Alex (posi) Newman
- Alex Breshears
- Alex Newman
- Ambreen Kazi
- Amit Kabra
- Andrei Savu
- Andrew Bayer
- Andrew Yao
- Andy Braslavskiy
- Ann McCown
- Antonio Bellezza
- Ashu Pachauri
- Atupal
- Avindra Goolcharan
- Ben Bishop
- Ben Gooley
- Ben White
- Bhargava Kalathuru
- Bruce Mitchener
- Bruno Mahé
- Chris Conner
- Chris Stephens
- Christopher Conner
- Christopher McConnell
- Christopherwq Conner
- Craig Minihan
- Daehan Kim
- Derek Chen-Becker
- Diego Sevilla Ruiz
- Dominik Gehl
- Eli Collins
- Enrico Berti
- Erick Tryzelaar
- Ewan Higgs
- Gilad Wolff
- Guido Serra
- Harsh
- Harsh J
- Henry Robinson
- Igor Wiedler
- Ilkka Turunen
- Istvan
- Ivan Orlov
- Jack McCracken
- Jaguar Xiong
- Jakub Kukul
- Jarcek
- Jenny Kim
- Joe Crobak
- Joey Echeverria
- Johan Ahlen
- Johan Åhlén
- Jon Natkins
- Josh Walters
- Karissa McKelvey
- Kevin Wang
- Kostas Sakellis
- Lars Francke
- Li Jiahong
- Linden Hillenbrand
- Luca Natali
- Luke Carmichael
- Marcus McLaughlin
- Mariusz Strzelecki
- Mathias Rangel Wulff
- Matías Javier Rossi
- Michael Prim
- Michal Ferlinski
- Michalis Kongtongk
- Mobin Ranjbar
- Nicolas Fouché
- NikolayZhebet
- Olaf Flebbe
- Oren Mazor
- Pala M Muthaia Chettiar
- Patricia Sz
- Patrycja Szabłowska
- Paul Battaglia
- Paul McCaughtry
- Peter Slawski
- Philip Zeyliger
- Piotr Ackermann
- Prachi Poddar
- Prakash Ranade
- Prasad Mujumdar
- Qi Xiao
- Renxia Wang
- Rick Bernotas
- Ricky Saltzer
- Romain Rigaux
- Roman Shaposhnik
- Rui Pereira
- Sai Chirravuri
- Scott Kahler
- Sean Mackrory
- Shahab Tajik
- Shawn Van Ittersum
- Shrijeet
- Shrijeet Paliwal
- Shuo Diao
- Siddhartha Sahu
- Simon Beale
- Simon Whittaker
- Stefano Palazzo
- Stephanie Bodoff
- Suhas Satish
- TAKLON STEPHEN WU
- Tatsuo Kawasaki
- Thomas Aylott
- Thomas Poepping
- Tianjin Gu
- Todd Lipcon
- Tom Mulder
- Vadim Markovtsev
- Wang, Xiaozhe
- Weixia Xu
- William Bourque
- Word
- Xavier Morera
- Xhxiong
- Yixiao Lin
- Yoer
- Yuriy Hupalo
- Zach York
- Zachary York
- Zhihai Xu
- abec
- airokey
- alheio
- alphaskade
- antbell
- arahuja
- bc Wong
- bcwalrus
- bwang
- cconner
- cmconner156
- cwalet
- dbeech
- fatherfox
- gdgt
- grundprinzip
- happywind
- jeff.melching
- krish
- linchan-ms
- lvziling
- motta
- mrmrs
- oxpa
- pat white
- peddle
- rainysia
- raphi
- robrotheram
- shobull
- sky4star
- spaztic1215
- thinker0
- todaychi
- van Orlov
- vinithra
- voyageth
- vybs
- wilson
- xq262144
- ywheel
- z-york
