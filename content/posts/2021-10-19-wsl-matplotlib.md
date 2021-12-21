---
title: "WSL Matplotlib Plot GUI"
date: 2021-10-19
categories:
  - note
tags:
  - wsl
  - python
  - matplotlib
toc: true
toc_label: "Outline"
toc_sticky: true
toc_icon: "box-open"
header:
  teaser: ./assets/teasers/code-bg.png

---

TL;DR

1. Install VcXsrv.
2. Install PyQT
3. Add following to shellrc

    ```bash
    export DISPLAY=`grep -oP "(?<=nameserver ).+" /etc/resolv.conf`:0.0
     ```

4. Open win firewall by:
Windows Security -> Firewall & network protection -> Allow an app through firewall -> make sure VcXsrv has both public and private checked. (When Launching xlaunch first time, you might get a prompt to allow through firewall.

5. Launch XLaunch with "Disable access control" ticked

### Reference
- [Show matplotlib plots (and other GUI) in Ubuntu (WSL1 & WSL2)](https://stackoverflow.com/questions/43397162/show-matplotlib-plots-and-other-gui-in-ubuntu-wsl1-wsl2)
