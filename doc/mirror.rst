Fetching existing sequence repositories
!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

A public instance of seqrepo with dated snapshots is available at on
seqrepo.biocommons.org.

You can list available snapshots like so::

  $ rsync rsync.biocommons.org::seqrepo                                                                                                                                                                                            
  This is the rsync service for tools and data from biocommons.org
  This service is hosted by Invitae (https://invitae.com/).
  
  drwxr-xr-x          4,096 2016/08/31 01:25:54 .
  dr-xr-xr-x          4,096 2016/08/28 03:25:40 20160827
  dr-xr-xr-x          4,096 2016/08/28 15:52:54 20160828

You may mirror the entire seqrepo archive or a specific snapshot, as
shown below::

  $ rsync -HRavP rsync.biocommons.org::seqrepo/20160828 /usr/local/share/seqrepo/                                                                                                                                                  
  This is the rsync service for tools and data from biocommons.org
  This service is hosted by Invitae (https://invitae.com/).

  receiving incremental file list
  20160828/
  20160828/aliases.sqlite3
  ...

If seqrepo is already installed, you may check the repo status with::

  seqrepo -d /usr/local/share/seqrepo/20160827 show-status
  seqrepo 0.2.2
  root directory: /home/reece/dl.biocommons.org/seqrepo/20160827/, 7.9 GB
  backends: fastadir (schema 1), seqaliasdb (schema 1) 
  sequences: 773494 sequences, 93002629585 residues, 188 files
  aliases: 5572583 aliases, 5473096 current, 9 namespaces, 773494 sequences

For other commands, see the `command line documentation <cli.rst>`__.

.. note:: seqrepo snapshot directories may be moved, renamed, or
          symlinked as needed.  All paths are stored relative to the
          snapshot root.