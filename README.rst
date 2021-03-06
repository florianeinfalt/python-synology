===========================
Python API for Synology DSM
===========================

.. image:: https://travis-ci.org/StaticCube/python-synology.svg?branch=master
    :target: https://travis-ci.org/StaticCube/python-synology

Installation
============

.. code-block:: bash

    [sudo] pip install python-synology


Usage
=====

Module
------

You can import the module as `SynologyDSM`.

.. code-block:: python

    from SynologyDSM import SynologyDSM

    print("Creating Valid API")
    api = SynologyDSM("<SynologyIp>", "<SynologyPort>", "<Username>", "<Password>")

    print("=== Utilisation ===")
    print("CPU Load:   " + str(api.utilisation.cpu_total_load) + " %")
    print("Memory Use: " + str(api.utilisation.memory_real_usage) + " %")
    print("Net Up:     " + str(api.utilisation.network_up()))
    print("Net Down:   " + str(api.utilisation.network_down()))
    
    print("=== Storage ===")
    volumes = api.storage.volumes
    for volume in volumes:
        print("ID:         " + str(volume))
        print("Status:     " + str(api.storage.volume_status(volume)))
        print("% Used:     " + str(api.storage.volume_percentage_used(volume)) + " %")

    disks = api.storage.disks
    for disk in disks:
        print("ID:         " + str(disk))
        print("Name:       " + str(api.storage.disk_name(disk)))
        print("S-Status:   " + str(api.storage.disk_smart_status(disk)))
        print("Status:     " + str(api.storage.disk_status(disk)))
        print("Temp:       " + str(api.storage.disk_temp(disk)))