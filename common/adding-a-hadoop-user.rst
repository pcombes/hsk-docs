Adding a Hadoop User
====================

You must add a user account for each Linux user that will submit
MapReduce jobs. The procedure below can be used to add a user named
hduser1.

#.  Add user to Isilon.
    
    .. parsed-literal::

      isiloncluster1-1# **isi auth groups create hduser1 --zone zone1 \\
      --provider local**
      isiloncluster1-1# **isi auth users create hduser1 --primary-group hduser1 \\
      --zone zone1 --provider local \\
      --home-directory /ifs/isiloncluster1/zone1/hadoop/user/hduser1**

#.  Add user to Cloudera nodes. Usually, this only needs to be performed on the master-0 node.
    
    .. parsed-literal::

      [root\@mycluster1-master-0 ~]# **adduser hduser1**

#.  Create the user's home directory on HDFS.
    
    .. parsed-literal::

      [root\@mycluster1-master-0 ~]# **sudo -u hdfs hdfs dfs -mkdir -p /user/hduser1**
      [root\@mycluster1-master-0 ~]# **sudo -u hdfs hdfs dfs -chown hduser1:hduser1 \\
      /user/hduser1**
      [root\@mycluster1-master-0 ~]# **sudo -u hdfs hdfs dfs -chmod 755 /user/hduser1**
