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
      name: hercules,
      group: hercules, 
      uid: 502, 
      gid: 502
    
    # Where to store e.g. downloaded rpms.
    hercules_tmp_path: /tmp/{{ hercules_user }}/files
    
    # Where the Scala Build Tool (SBT) RPM can be obtained.
    hercules_sbt_download_site: https://dl.bintray.com/sbt/rpm/
    
    # The version of the SBT rpm to download.
    hercules_sbt_version: 0.13.5
    
    # The SHA256 hash of the corresponding SBT RPM.
    hercules_sbt_sha256sum: d88705835c4a94a8a3a6627e00d19124eae1aa2d573640e203723473de9a89d8
    
    # Path on the host to the hercules rpm
    hercules_rpm_path: files/hercules-0.1.rpm
    
    # The github url for the Hercules fork.
    hercules_git_url: https://github.com/Molmed/hercules
    
    # The git tag for the Hercules code to obtain. This can be a tag, release, commit, "HEAD" etc.
    hercules_git_release: a52356af8f02b0647182eae04088dc1f6104358c
    
    # If a RPM for the specified hercules release is available on github, the SHA256 hash should be specified here.
    hercules_git_release_sha256sum: .

 
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

