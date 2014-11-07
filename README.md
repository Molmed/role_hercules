Hercules
========

This is a public role for deploying the Hercules system, developed and used in production by the SNP&SEQ Technology Platform, a partner in the Swedish National Genomics Infrastructure (NGI), hosted at Science For Life Laboratory (SciLifeLab, http://www.scilifelab.se). Hercules is a system for managing sequencing data in the context of a sequencing facility.

Requirements
------------

CentOS 6

Role Variables
--------------

The following variables (and corresponding default values) are used by the role:


    # The user under which to install and run. Will be created if not present.
    hercules_user:
      name: hercules
      group: hercules 
      uid: 502
      gid: 502
      
    # Where to store e.g. downloaded rpms.
    hercules_tmp_path: /tmp/{{ hercules_user.name }}/files
    
    # Where the Scala Build Tool (SBT) RPM can be obtained.
    hercules_sbt_download_site: https://dl.bintray.com/sbt/rpm/
    
    # The version of the SBT rpm to download.
    hercules_sbt_version: 0.13.5
    
    # The SHA256 hash of the corresponding SBT RPM.
    hercules_sbt_sha256sum: d88705835c4a94a8a3a6627e00d19124eae1aa2d573640e203723473de9a89d8
    
    # Path on the host to the hercules rpm
    hercules_rpm_path: files/hercules-0ea92d52e0e9c3ca65ae9f50737fe04e977e320f.rpm
    
    # The github url for the Hercules fork.
    hercules_git_url: https://github.com/Molmed/hercules
    
    # The git release to look for an available rpm on github for. 
    hercules_git_release: 0.1
    
    # If a RPM for the specified hercules release is available on github, the SHA256 hash should be specified here.
    hercules_git_release_sha256sum: .

Note that a Hercules RPM can be supplied either as a file existing on the host (using the hercules_rpm_path variable), or as release version (using the hercules_git_release variable). For the last case, this requires that a corresponding RPM is available on GitHub, attached to the release. The role will first attempt to obtain the RPM from GitHub and, if failing, it will attempt to get the file from the host.

Dependencies
------------

No dependencies

Example Playbook
----------------

    - hosts: servers
      roles:
         - { role: 'hercules', hercules_git_release: '0.1' }

License
-------

MIT

Author Information
------------------

Pontus Larsson, http://www.sequencing.se

