# apt gives “Unstable CLI Interface” warning
================================

**Author**: Lien Chen  **Date**: 2020-07-29

With build the docker-slim using `apt install PKG` run out with warning.
Thought that **apt is a subset of apt-get and apt-cache commands providing necessary commands for package management**
So it might docke-slim prefer to use apt-get or apt-cache to work.
Just Run the command with `apt-get [command]`, the warning will remove.

---
#### Reference
* [apt gives “Unstable CLI Interface” warning](https://askubuntu.com/questions/990823/apt-gives-unstable-cli-interface-warning)
* [Difference Between apt and apt-get Explained](https://itsfoss.com/apt-vs-apt-get-difference/)