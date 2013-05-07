Multi-threaded-downloader (0.0.1)
=================================

This is a multi threaded downloader which is made in nodejs. It is highly configurable and extremely efficient.

Features
--------
1. Supports virtually unlimited number of threads.
2. Supports restarting of failed downloads (Downloads only the parts that were not downloaded).
3. Supports checksum verification of file download.


How to use
----------
1. Install Nodejs (skip if already done).
2. Clone the repository.

	```bash
	git clone https://github.com/tusharmath/Multi-threaded-downloader.git
	```
3. Navigate to the root folder of the project.
4. Create a global command line alias.

	```bash
	npm link
	```
5. Start using eg.

	```bash
	mtd -u "http://mirror.switch.ch/ftp/mirror/videolan/vlc/2.0.6/macosx/vlc-2.0.6.dmg" -p "vlc-2.0.6.dmg"
	```

6. Open the Config.json for configuring your downloads.


Upcoming features!
-------------------
1. Create a user interface.

2. Have different video download algorithms to boost up video download performance.

3. Work as a proxy with video sites such as youtube so that buffering is completely removed.

4. Will be able to restart abruptly terminated threads.

5. Able to install through node package manager.

6. Supports partial downloads for eg - downloading from 30 to 70% of the complete file.