
.. _spi-flash-test:

SPI-Flash Test
###############

Overview
********

This is the test application to test and verify the copying of data from the OSPI flash to the PSRAM XiP window.
The test also verifies the read/write operations on the OSPI flash.
Tested on the Alif B1 DK board with the OSPI flash and PSRAM devices.

Layout produced by test_4mb.bin: 8-byte magic, offset-encoded words, CRC32 tail.
#define TEST_MAGIC		"ALIFPSRM"
#define TEST_MAGIC_LEN		8U

Building and Running
********************

Copy the testbin_4mb.bin to the OSPI flash.
The testbin_4mb.bin file is located in the build directory after building the application.

Example command to build in sdk root directory:

.. code-block:: console

   west build -b alif_b1_dk/ab1c1f4m51820ph0/rtss_he ./alif/samples/drivers/spi_flash -p

Flash the test application:

.. code-block:: console

   west flash

Sample Output
=============

.. code-block:: console

	main: start
	copy: 4194304 bytes flash@0x0 -> psram@0x0 (chunk 8192B)
	copy: done (4194304 bytes, bus left in PSRAM XiP mode)
	verify: magic OK (ALIFPSRM)
	verify: offset-word pattern OK (0x8..0x3ffff8)
	verify: crc32 OK (calc 0xafb7a905, stored 0xafb7a905)
	verify: PASS -- 4194304 bytes copied to PSRAM XiP @0xa0000000
