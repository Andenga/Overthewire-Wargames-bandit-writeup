Over the Wire Bandit Write Up
6–10	Searching and filtering

11–13	Encoding and transformations

14–17	Networking basics

18–20	SSH and restricted shells

21–26	Automation and cron jobs

27–34	Git and source control

  - 6–10	Searching and filtering
  - 11–13	Encoding and transformations
  - 14–17	Networking basics
  - 18–20	SSH and restricted shells
  - 21–26	Automation and cron jobs
  - 27–34	Git and source control


site_name: Overthewire Bandit interactive write-up

theme:
  name: material


markdown_extensions:
  - attr_list
  - toc:
      permalink: true
      toc_depth: 2

extra_css:
  - stylesheets/extra.css

  nav:
  - Home: index.md
  - Categories:
    - SSH login basics: index.md#level-0
    - File navigation & inspection: index.md#level-3
    - Searching and filtering: index.md#level-6
    - Encoding and transformations: index.md#level-8
    - SSH keys, networking basics, and diffing files: index.md#level-14
    - Restricted shells and setuid basics: index.md#level-19
    - Cron jobs, brute-forcing, and shell escapes: index.md#level-22
    - Git and source control: index.md#level-28
    - Restricted shell / sandbox escape: index.md#level-32