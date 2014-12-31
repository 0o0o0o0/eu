################################################################################
# 
#  Copyright (c) 2011, EURid. All rights reserved.
#  The YADIFA TM software product is provided under the BSD 3-clause license:
# 
#  Redistribution and use in source and binary forms, with or without 
#  modification, are permitted provided that the following conditions
#  are met:
# 
#         * Redistributions of source code must retain the above copyright 
#           notice, this list of conditions and the following disclaimer.
#         * Redistributions in binary form must reproduce the above copyright 
#           notice, this list of conditions and the following disclaimer in the 
#           documentation and/or other materials provided with the distribution.
#         * Neither the name of EURid nor the names of its contributors may be 
#           used to endorse or promote products derived from this software 
#           without specific prior written permission.
# 
#  THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS "AS IS"
#  AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT LIMITED TO, THE 
#  IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE ARE
#  DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT HOLDER OR CONTRIBUTORS BE LIABLE 
#  FOR ANY DIRECT, INDIRECT, INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL 
#  DAMAGES (INCLUDING, BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR 
#  SERVICES; LOSS OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER
#  CAUSED AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT LIABILITY,
#  OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY WAY OUT OF THE USE
#  OF THIS SOFTWARE, EVEN IF ADVISED OF THE POSSIBILITY OF SUCH DAMAGE.
# 
################################################################################

20141216:
        YADIFA 2.0.4

        This release is a public release.

        By popular demand, the default log file directory is now PREFIX/var/log/yadifa.  It can be set using --with-logdir=/my/dir

        Improved build mechanism.
            It has been tested to work automatically on Linux, FreeBSD, OSX, SunOS.
            RedHat familly builds will use -O2 as maximum optimisations.

            Note that some optional features are now enabled by default but can be disabled.

        Fixes:
        - fixed an issue with the AXFR transfer where the serial number would not be properly taken into account
        - fixed an issue with the notify mechanism that could occur if the server was only listening to 127.0.0.1 
        - fixed an issue with bogus DNSKEY records that may potentially lead to a crash in openssl
        - fixed a reported potential "tmpfile" vulnerability on DEBUG builds (generated with make debug)
        - fixed an issue with IPv6 connections on some architectures
        - typos fixes
        - minor fixes and improvements

20141104:
        Architecture portability enhancements.

        On Solaris, if no --enable-force32bits nor --enable-force64bits is set, then 64 bits will be forced (fixes an issue at link-time)

        ELF 64-bit MSB executable SPARCV9 Version 1, UltraSPARC3 Extensions Required, dynamically linked, not stripped, no debugging information available

        PATH=/opt/csw/bin:/usr/ccs/bin:$PATH ./configure --enable-force32bits
        PATH=/opt/csw/bin:/usr/ccs/bin:$PATH make

20141030:
        Architecture portability enhancements.

    FreeBSD 9
        FreeBSD dnode3 9.0-RELEASE-p3 FreeBSD 9.0-RELEASE-p3 #0: Tue Jun 12 02:52:29 UTC 2012     root@amd64-builder.daemonology.net:/usr/obj/usr/src/sys/GENERIC  amd64
        gcc (GCC) 4.2.1 20070831 patched [FreeBSD]
        ELF 64-bit LSB executable, x86-64, version 1 (FreeBSD), dynamically linked (uses shared libs), for FreeBSD 9.0 (900044), not stripped

    Ubuntu
        Linux dnode10 3.2.0-49-generic #75-Ubuntu SMP Tue Jun 18 17:39:32 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
        gcc (Ubuntu/Linaro 4.6.3-1ubuntu5) 4.6.3
        ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0xe3b8601b9b5e59f8c9ce519cacbe9b8ff544ff1d, not stripped

    OSX
        Darwin RD-Mac-Mini.local 13.3.0 Darwin Kernel Version 13.3.0: Tue Jun  3 21:27:35 PDT 2014; root:xnu-2422.110.17~1/RELEASE_X86_64 x86_64
        Apple LLVM version 5.1 (clang-503.0.40) (based on LLVM 3.4svn)
        Mach-O 64-bit executable x86_64

20141029:
        Architecture portability enhancements.

        uname -a
        gcc --version
        file yadifad

    YellowDog Linux
        Linux 2.6.29-3.ydl61.4 #1 SMP Mon Sep 7 14:50:27 PDT 2009 ppc64 ppc64 ppc64 GNU/Linux
        gcc (GCC) 4.1.2 20080704 (Red Hat 4.1.2-44)
        ELF 32-bit MSB executable, PowerPC or cisco 4500, version 1 (SYSV), for GNU/Linux 2.6.9, dynamically linked (uses shared libs), for GNU/Linux 2.6.9, not stripped

        note: using --enable-force64bits failed because of ssl, no simple/quick way to install openssl-devel.ppc64 seemed available

    Debian PPC64
        Linux 3.2.0-3-powerpc64 #1 SMP Mon Jul 23 08:03:56 UTC 2012 ppc64 GNU/Linux
        gcc (Debian 4.6.3-8) 4.6.3
        ELF 32-bit MSB executable, PowerPC or cisco 4500, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.26, BuildID[sha1]=0xedc47c984a4af7eb9a7ecbc0f135e4d064ba08f0, with unknown capability 0x41000000 = 0x13676e75, with unknown capability 0x10000 = 0xb0401, not stripped

        note: using --enable-force64bits failed because of ssl, no simple/quick way to install openssl-devel.ppc64 seemed available

20140905:
    YADIFA 2.0.0

    This release is a public release

    Fixes:
    - fixed a log incorrectly reporting an error when the client didn't close the TCP connection fast enough
    - fixed an issue with the statistics on TCP queries

    Known issue:
    - removing the last key of a signed zone is permitted by YADIFA but triggers some chicken-egg issue with signatures.

20140829:
    YADIFA 2.0.0-beta3-public

    This release is a public release

    - --disable-master feature at configure now builds a slave-only server

    Fixes:
    - fixed an issue with TSIG signed queries
    - fixed an issue with thread pool live resizing
    - fixed an issue where reading an undeleted obsolete journal ending at the start of a newly transferred zone from the master would incorrectly trigger an error

    Known issue:
    - removing the last key of a signed zone is permitted by YADIFA but triggers some chicken-egg issue with signatures.


20140630:
    YADIFA 2.0.0-beta2-public

    This release is a public release

    - basepath disabled
    - pidpath removed, only pidfile remains
    - log reopen notification is now timestamped
    - slave zones no longer complain about missing NSEC/NSEC3 private keys
    - the error code ZRE_FILE_NOT_FOUND has been replaced by the more accurate code ZRE_NO_VALID_FILE_FOUND
    - default logging settings no longer output debug

    Fixes:
    - fixed issue in flag computation (AD,CD)
    - fixed an issue with journal truncation sometimes leading to a crash
    - zone parsing now correctly accepts '#' as a comment marker
    - zone parsing now rejects wrong fqdn as soon as it reads them, leading to a more accurate error message
    - removing the last dnskey of a zone no longer crashes the server

    Known issue:
    - removing the last key of a signed zone is permitted by YADIFA but triggers some chicken-egg issue with signatures.

    yadifa remote client commands prototype is now available with the following supported commands:

        -shutdown
            shuts down yadifa
            e.g. ./yadifa -s "192.0.2.1 port 53" -t shutdown
            
        -cfgreload
            reloads the <key> and <zone> sections of the yadifad configuration

            e.g. ./yadifa -s "192.0.2.1 port 53" -t cfgreload

        -logreopen
            closes and reopen the log files

            e.g. ./yadifa -s "192.0.2.1 port 53" -t logreopen

        -freezeall
            prevents all zones from being updated dynamically with nsupdate
            
            e.g. ./yadifa -s "192.0.2.1 port 53" -t freezeall

        -freeze
            prevents a zone from being updated dynamically with nsupdate

            e.g. ./yadifa -s "192.0.2.1 port 53" -t freeze -q somedomain.eu

        -unfreezeall
            enables updates of all zones again

            e.g. ./yadifa -s "192.0.2.1 port 53" -t unfreezeall

        -unfreeze
            enables updates of a zone again

            e.g. ./yadifa -s "192.0.2.1 port 53" -t unfreeze -q somedomain.eu

        In order to work, the allow-control ACL must be defined either in <main> for the global commands and
        may also be defined in <zone> for the ones targeting a specific zone.

            e.g. allow-control 127.0.0.1

        Note that tsig is not supported in the client yet.

20140528:
    YADIFA 2.0.0-beta1-public

	This release is a public release

	- NSID implemented (enabled at ./configure time with --enable-nsid
        - generic parser for:
 		- getops
		- zone file
		- resolv.conf
		- configuration
	- '@' can now be used in a zone file
        - new binary for controlling 'yadifad' (yadifa)
        - framework is rewritten for multi core systems
        - single core server has been removed

    Fixes:	
	- fixed several minor issues

    Know issues:
	- removing all dnskeys from a zone file crashes the server
	- yadifa has some issues with nodelay, nocork
	
20130424:
    YADIFA 1.1.0
        _ added DSA signature
        _ added SHA-256 SHA-384 SHA-512 digest algorithms
        _ now supports additional DNSSEC algorithms:
            DSASHA1
            DSASHA1_NSEC3
            RSASHA256_NSEC3
            RSASHA512_NSEC3
        _ Respone Rate Limitation implemented (enabled at ./configure time with --enable-rrl)
        _ --enable-tiny-footprint now reduces the memory usage further by reducing the standard log queue from 2^20 to 2^12 entries
        _ the general speed has been slightly improved
        _ dynamic updates pending for more than 3 seconds are now dropped with an error
        _ dynamic provisioning
    Fixes:
        _ fixed a memory leak that could occur at NSEC3 generation when loading the zone failed in a particular way
        _ fixed a memory leak at ixfr send
        _ fixed handling of '_' character that was improperly stored in the database
        _ fixed bandwidth limit settings (tcp stream in and out) not always being taken from the configuration
        _ fixed TSIG answer verification for notifies
        _ fixed error codes not being registered and thus logged as unknown hexadecimal error code.
        _ other minor fixes

20130612:
    YADIFA 1.0.3
        Fixes only (backports from 1.1.0)

    Fixes:
        _ fixed an issue preventing YADIFA from being build from another directory
        _ fixed an issue with OSX systems where gsed has to be used instead of sed
        _ fixed an issue with the '_' character not being properly handled
        _ fixed an issue where reading MX record from a zone file would incorrecly be rejected as invalid
        _ fixed an issue where the OPT record would not be properly written
        _ fixed an issue where an undefined ACL reference would be silently ignored
        _ fixed missing code tags for several error codes.  From now on unregistered codes are dumped in hexadicimal.
        _ fixed portability issues with BSD and OSX
        _ fixed several minor issues


20120921:
    YADIFA 1.0.2
        Fixes only

    Fixes:
        _ fixed an issue where the journal file was sometimes not properly closed at the end of a task
        _ fixed an issue where the TCP usage slots would sometimes wrongly return that they were all being used
        _ fixed an issue on IXFR processing (slave side) where the type of answer from the master would not be properly detected
        _ fixed an issue with TSIG on secrets not exactly 16 bytes long (binary form)
        _ fixed an issue on 32 bits architectures where the sig-validity-* fields would not be properly handled if not set
          on each zone section.
        _ slightly improved the replay time of big journal files
        _ fixed several minor issues

    Known issues:
        _ if the serial of a zone is changed in a way that it goes beyond a value such as
          the journal serial start is bigger than the journal serial end, issues are expected
          for IXFR answers.
        _ notify is ignored on TCP  

20120709:
	YADIFA 1.0.1
		_ logging repeat compression is now by channel instead of global

	Fixes:
        _ fixed an issue where glibc whould assert if libgcc_s.so (libgcc_s.so.1) and libc.so (libc.so.6) where not
		  available inside the chrooted directory of YADIFA
		_ fixed an issue in the syslog module

	Known issues:
		_ on 32 bits architectures, the sig-validity-* fields are not properly copied from <main> to <zone>
		  as a workaround, set the sig-validity fields in each <zone> container in 32 bits architectures

		  ie:
			  sig-validity-interval 7
 			  sig-validity-regeneration 168
			  sig-validity-jitter 3600
		_ if the serial of a zone is changed in a way that it goes beyond a value such as
		  the journal serial start is bigger than the journal serial end, issues are expected
		  for IXFR answers.
		_ notify is ignored on TCP

20120625:
	YADIFA 1.0.0
		_ LTO support can be enabled with --enable-lto but this is not working with clang. LTO does not increase
		  the performance significally
		_ parallel processing of listening addresses can now be enabled.
		  It can be set using thread-count-by-address in the <main> section.
		  By default YADIFA will not use parallel processing as this feature has not been
		  as thoroughly tested as the single-thread processing model
		_ default parameters tuning
		_ fixes

	 Known issue:
		_ on 32 bits architectures, the sig-validity-* fields are not properly copied from <main> to <zone>
		  as a workaround, set the sig-validity fields in each <zone> container in 32 bits architectures

		  ie:
			  sig-validity-interval 7
 			  sig-validity-regeneration 168
			  sig-validity-jitter 3600
		
20120530:
	YADIFA 1.0.0RC3
		_ the configuration parser now ignores undefined logger names and
		  report them with a warning
		_ syslog messages are now put in the name of "yadifad" instead of  the name used for the "syslog" channel
		_ syslog messages do not print the time from YADIFA anymore
		_ improved the steps involved in loading a locally cached slave zone
		_ zones are now loaded in background 
		_ man page yadifad-conf.man5 renamed into yadifad.conf.man5

	Fixes:
		_ AXFR/IXFR answers with the RA bit set are nolonger rejected as invalid
		_ YADIFA now answers to SIGINT again (shutdown)
		_ fixed an issue where obsolete AXFR files were not always being deleted
		_ fixed an issue occurring when both IPv4 and IPv6 were available to handle a notify
		_ fixed journal replay issue where some RRSIGs records were not properly removed
		_ fixed an issue occurring with IPv6 queries
		_ fixed an issue in the generation of a specific NSEC3 error answer
		_ fixed named query style layout

	Known issue:
		_ if the serial of a zone is changed in a way that it goes beyond a value such as
		  the journal serial start is bigger than the journal serial end, issues are expected
		  for IXFR answers.
		_ notify is ignored on TCP
		
20120328:
	YADIFA 1.0.0RC2
		_ fixed logging issue on work file creation error
		_ fixed an issue where IXFR queries could be rejected as being wrongly formatted
		_ fixed an issue in the query logging text
		_ enabled command line options ( -u uid -g gid -d )
	
20120319:
	YADIFA 1.0.0RC1

	Is a full functional authoritative name server:

		- works as primary or secondary name server
		- AXFR
		- IXFR
		- NOTIFY
		- NSUPDATE
		- TSIG
		- CLASSES:
			- IN
			- CH (just for version)
		- TYPES:
			- AAAA
			- CNAME
			- DNSKEY
			- DS
			- HINFO
			- MX
			- NAPTR
			- NS
			- NSEC3
			- NSEC3PARAM
			- NSEC
			- PTR
			- RRSIG
			- SOA
			- SRV
			- SSHFP
			- TXT
		- Automatic resigning
		- DNSSEC algorithms:
			- 5 (RSASHA1)
			- 7 (RSASHA1-NSEC3
		- ACL's
	

	KNOWN ISSUES:

		NSEC3:	_ cannot work with multiple NSEC3PARAM chains with mixed OPT-IN/OUT settings

			_ adding a new NSEC3 chain expects that the master sends the NSEC3PARAM first (it does not seems to be always the case)
				  We have a case where a master starts with 2 thousands NSEC3 opt-out records then adds 6 millions NSEC3 opt-in records but does not give the NSEC3PARAM record
				  first. The slave server rejects them all because it's unable to link them to a chain.  (This one has high priority)

		DNSSEC:	_ it is not allowed to change the zone security mode (unsecure, NSEC, or NSEC3).  Once the zone is loaded it keeps its security mode.

			_ dynamic updates of NSEC as well as NSEC3 records are refused

		QUIT:	the server will shutdown on the following conditions:

			_ detection of an impossible situation or an internal integrity issue (ie: for any reason the SOA has vanished from a zone)

			_ memory limit reached which prevents any more work

			_ ipc issue which prevent internal services communication

		ACL:	_ since the access control is set by zone and CHAOS class is not implemented as a configurable zone, it is not possible (yet) to specifically block CHAOS queries.

20111121:
	YADIFA 0.5.5
		-	many fixes 

	KNOWN ISSUE: NSEC3 slave zone replay fails.

20110706:
	YADIFA 0.5.0
		-	slave mode, AXFR/IXFR (no TSIG yet for the slave-side transfer)
		-	answers to a notify from the master
		-	polls the (first) master on the masters list
		-	maintains the .axfr & .ix files (deletes the obsoletes ones)
		-	TSIG queries are checked
		-	Replays the zone journal on startup after the zone load (journaling)
		-	Answers IXFR queries (journaling)

20110601:
	YADIFA 0.4.0
		Operational:
		-	It works as a no dnssec name server
		-	No notifies to slave name servers
		-	daemon
		-	Answers AXFR queries with TSIG
		- 	nsupdate functionality (journaling)
		-	TSIG on client server side will be transmitted, but not checked
		-	ACL works
		- 	The zone has SOA, NS A resource records.

20110524:
	YADIFA 0.3.0
		First release internally of yadifad 20110524115500 GMT+1.

		Operational:
		-	It works as a no dnssec name server
		-	No notifies to slave name servers
		-	daemon
		-	Answers AXFR queries
		- 	The zone has SOA, NS A resource records.
		

20091224:
	YADIFA 0.2.0
		_	Answers AXFR queries
		_	ACL based on IP and TSIG (not all query types are ACL'ed yet)

20091104:
	YADIFA 0.1.0

		YADIFA is a work in progress. The main goal is to have an alternative for BIND or NSD.

		Version 0.1.0 is an authoritative server only. 

		It has no:
		-	AXFR/IXFR functionality
		-	dynupdate
		- 	support for NSEC
		- 	support for NSEC3
		-	caching mechanism
		- 	additional tools (eg.dig, dnssectools, drill,...)

		It has:
		-	a very fast way to give authoritative answer
		-	a very fast method for loading the database and checking the zone files

		This first release is to have a feeling how it works in an operational environment.
	
	TODO

		Everything what is not implemented, has to be implemented. Most of the code is there, but is not activated.

		No comformity tests has been done. (This of course is on the todo list)



Bug Reports and Mailing Lists

        Bugs reports should be sent to

                bugreport@yadifa.eu


################################################## ##############################
＃
＃版权所有（C）2011，EURid。版权所有。
＃在YADIFA TM软件产品是根据BSD3条许可提供：
＃
＃再分配和使用源代码和二进制的形式，有或无
＃修改，都允许设置下列条件
＃得到满足：
＃
＃*重新分发源代码必须保留以上版权
＃通知，此条件列表及以下免责声明。
＃*以二进制形式重新分发必须复制上述版权
＃通知，此条件列表和以下免责声明
＃文档和/或提供与分发的其他材料。
＃* EURid的无论是名称及其贡献者的名称可能是
＃用于宣传或推销本软件的衍生产品
＃没有事先书面许可。
＃
＃本软件由版权所有者和贡献者“AS IS”
＃任何明示或默示的担保，包括但不限于
针对特定用途的＃适销性和适用性的担保是
＃承担责任。在任何情况下，版权持有人或贡献者均不
＃的任何直接，间接，偶然，特殊，惩戒性，或者后果性
＃损失（包括但不限于，采购替代商品，
＃服务;使用，数据，或利润损失;或业务中断）
＃造成的，基于何种责任理论，无论是合同，严格责任，
＃还是侵权（包括疏忽或其他原因）而产生的使用以任何方式OUT
＃本软件，即使已被告知发生此类损害的可能性。
＃
################################################## ##############################

20141216：
        YADIFA2.0.4

        此版本是公开发布。

        应广大用户要求，默认的日志文件目录现在PREFIX的/ var/日志/ yadifa。它可以使用--with-LOGDIR=/我的/目录设置

        提高构建机制。
            它已经过测试，在Linux，FreeBSD，OSX，SunOS的自动工作。
            红帽法米利构建将使用-O2作为最大的优化。

            需要注意的是一些可选功能，默认情况下启用的，现在却可以被禁用。

        修正：
         - 修正了一个与AXFR转移那里的序列号不会被适当考虑
         - 修正了一个问题，通知机制可能发生，如果服务器只能听127.0.0.1
         - 修正了一个与虚假记载DNSKEY可能潜在地导致OpenSSL的崩溃
         - 修正了一个潜在的报道“TMPFILE”关于DEBUG漏洞构建（使用make调试生成）
         - 对某些架构IPv6连接固定的问题
         - 修正错别字
         - 小的修复和改进

20141104：
        建筑便携性增强。

        在Solaris上，如果没有--enable-force32bits也不--enable-force64bits设置，那么64位将被强制（在链接时修复的问题）

        ELF64位MSB可执行SPARCV9第1版，UltraSPARC3扩展需要的，动态链接的，不剥离，不提供调试信息

        PATH=/选择/ CSW/斌：的/ usr/ CCS /斌：$ PATH时候使用./configure --enable-force32bits
        PATH=/选择/ CSW/斌：的/ usr/ CCS /斌：$ PATH化妆

20141030：
        建筑便携性增强。

    FreeBSD的9
        FreeBSD的dnode39.0-RELEASE-P3的FreeBSD9.0-RELEASE-P3＃0：周二6月12日2时52分29秒UTC2012 root@amd64-builder.daemonology.net：的/ usr/ OBJ的/ usr/ src目录/ SYS/ GENERIC AMD64
        海湾合作委员会（GCC）4.2.120070831修补[FreeBSD的]
        ELF64位LSB的可执行文件，X86-64，版本1（FreeBSD的），动态链接（使用共享库），为FreeBSD9.0（900044），不剥离

    Ubuntu的
        Linux的dnode103.2.0-49泛型＃75，Ubuntu的SMP周二6月18日十七时39分32秒UTC2013 x86_64的x86_64的x86_64的GNU/ Linux的
        海湾合作委员会（Ubuntu的/ Linaro的4.6.3-1ubuntu5）4.6.3
        ELF64位LSB的可执行文件，X86-64，版本1（SYSV），动态链接（使用共享库），为GNU / Linux2.6.24，BuildID[SHA1]=0xe3b8601b9b5e59f8c9ce519cacbe9b8ff544ff1d，不剥离

    OSX
        达尔文RD-MAC-Mini.local13.3.0 Darwin内核版本13.3.0：周二6月3日21时27分35秒PDT2014年;根：XNU-2422.110.17〜1/ RELEASE_X86_64 x86_64的
        苹果LLVM5.1版本（铛-503.0.40）（基于LLVM3.4svn）
        Mach-O的64位可执行x86_64的

20141029：
        建筑便携性增强。

        -a的uname
        海湾合作委员会 - 版本
        文件yadifad

    YellowDog的Linux
        Linux的2.6.29-3.ydl61.4＃1 SMP周一9月7日14点五十分27秒PDT2009年PPC64 PPC64 PPC64的GNU / Linux
        海湾合作委员会（GCC）4.1.220080704（红帽4.1.2-44）
        ELF32位MSB可执行的PowerPC或Cisco4500，版本1（SYSV），为GNU / Linux2.6.9，动态链接（使用共享库），为GNU / Linux2.6.9，不剥离

        注意：使用--enable-force64bits由于SSL失败，安装OpenSSL的-devel.ppc64没有简单/快速的方式似乎可用

    Debian的PPC64
        Linux的3.2.0-3-powerpc64＃1 SMP周一7月23日8时03分56秒UTC2012 PPC64的GNU / Linux
        海湾合作委员会（Debian的4.6.3-8）4.6.3
        ELF32位MSB可执行的PowerPC或Cisco4500，版本1（SYSV），动态链接（使用共享库），为GNU / Linux2.6.26，BuildID[SHA1]=0xedc47c984a4af7eb9a7ecbc0f135e4d064ba08f0，未知功能0x41000000=0x13676e75，未知能力0x10000处=0xb0401，不剥离

        注意：使用--enable-force64bits由于SSL失败，安装OpenSSL的-devel.ppc64没有简单/快速的方式似乎可用

20140905：
    YADIFA2.0.0

    此版本是公开发布

    修正：
     - 修正了一个错误日志报告错误时，客户端没有关闭TCP连接速度不够快
     - 对TCP查询统计修正了一个问题

    已知的问题：
     - 删除签名区域的最后一个键被YADIFA允许的，但与签名会触发一些鸡还是先有蛋的问题。

20140829：
    YADIFA2.0.0-β3公开

    此版本是公开发布

     - 在配置--disable主功能现在建立一个从专用服务器

    修正：
     - 修正了一个与TSIG签订查询
     - 修正了一个与线程池调整大小直播
     - 修正了一个问题，即在阅读新传输的区域开始从主结束会错误地触发一个错误的未删除过时的日记

    已知的问题：
     - 删除签名区域的最后一个键被YADIFA允许的，但与签名会触发一些鸡还是先有蛋的问题。


20140630：
    YADIFA2.0.0-β2公开

    此版本是公开发布

     - basepath禁用
     - pidpath去掉，只遗存了pidfile
     - 重新登录通知现在时间戳
     - 从区域不再抱怨缺少NSEC/ NSEC3私钥
     - 错误代码ZRE_FILE_NOT_FOUND已取代了更精确的代码ZRE_NO_VALID_FILE_FOUND
     - 默认的日志记录设置不再输出调试

    修正：
     - 旗计算固定的问题（AD，CD）
     - 修正了一个与杂志截断有时会导致崩溃
     - 区域分析现在可以正确地接受'＃'作为一个注释标记
     - 区域分析，现在只要读取他们拒绝错误的FQDN，从而更准确的错误信息
     - 除去一个区段的最后DNSKEY不再崩溃服务器

    已知的问题：
     - 删除签名区域的最后一个键被YADIFA允许的，但与签名会触发一些鸡还是先有蛋的问题。

    yadifa远程客户端命令的原型现在可与以下支持的命令：

        -关闭
            关闭yadifa
            例如./yadifa-s“192.0.2.1端口53”-t关闭
            
        -cfgreload
            重新加载<key>和<区>的yadifad配置的部分

            例如./yadifa-s“192.0.2.1端口53”-t cfgreload

        -logreopen
            关闭并重新打开日志文件

            例如./yadifa-s“192.0.2.1端口53”-t logreopen

        -freezeall
            防止被动态更新的nsupdate所有区域
            
            例如./yadifa-s“192.0.2.1端口53”-t freezeall

        -freeze
            防止被动态更新的nsupdate区

            例如./yadifa-s“192.0.2.1端口53”-t冻结-q somedomain.eu

        -unfreezeall
            使所有区域再次更新

            例如./yadifa-s“192.0.2.1端口53”-t unfreezeall

        -unfreeze
            使一个区域的再次更新

            例如./yadifa-s“192.0.2.1端口53”-t解冻-q somedomain.eu

        为了工作，可以控制ACL必须为全局命令定义无论是在<主>和
        还可以在<区>定义为那些针对特定区域。

            例如允许控制127.0.0.1

        需要注意的是TSIG不支持在客户端尚未。

20140528：
    YADIFA2.0.0-β1公开

此版本是公开发布

- NSID实施（在的./configure时启用--enable-NSID
         - 通用解析器：
  - getops
- 区域文件
- 的resolv.conf
- 配置
- “@”现在可以在区域文件中使用
         - 控制“yadifad”新二元（yadifa）
         - 框架改写为多核心系统
         - 单核服务器已被删除

    修正：
- 修正了几个小问题

    知道的问题：
- 从区域文件删除所有dnskeys崩溃的服务器
- yadifa与NODELAY，nocork一些问题

20130424：
    YADIFA1.1.0
        _添加DSA签名
        _添加SHA-256 SHA-384 SHA-512摘要算法
        _现在支持额外的DNSSEC算法：
            DSASHA1
            DSASHA1_NSEC3
            RSASHA256_NSEC3
            RSASHA512_NSEC3
        _ Respone速率限制实现的（在的./configure时使用--enable-RRL启用）
        _--enable-微小的足迹，现在进一步降低了标准日志队列从2^20〜2^12项减少了内存占用
        _一般的速度已略有改善
        _动态更新待定的3秒以上，现在降到一个错误
        _动态配置
    修正：
        _固定可能发生在NSEC3代，当加载区域失败以特定方式内存泄漏
        _固定在IXFR发送内存泄漏
        _的“_”字符的固定的处理被不正确地存储在数据库中
        _固定带宽限制设置（TCP流出来）并不总是采取从配置
        _固定TSIG答案核查通知
        _固定的错误代码没有被注册，因而记录为未知的十六进制错误代码。
        _其他小的修正

20130612：
    YADIFA1.0.3
        仅修复（反向移植从1.1.0）

    修正：
        _固定一个问题阻止YADIFA被建立从另一个目录
        _固定一个问题OSX系统，其中gsed必须使用代替的sed
        _用'_'字没有被妥善处理，修复的问题
        _固定在那里读书MX记录从区域文件将incorrecly被拒绝为无效的问题
        _固定在那里的OPT记录将无法正确写入的问题
        _固定在那里一个未定义的ACL引用将被忽略的问题
        _固定缺少代码标签数错误代码。从现在起，未经注册的代码会被弃置在hexadicimal。
        _与BSD和OSX固定可移植性问题
        _固定的几个小问题


20120921：
    YADIFA1.0.2
        仅修复

    修正：
        _固定在那里的日志文件有时无法正常在任务结束时关闭问题
        _固定的一个问题，即TCP使用的插槽有时会错误地返回，他们都正在使用
        _对IXFR处理（从侧面），其中的答案从主类型将无法正确检测修正了一个问题
        _的秘密不完全16字节长（二进制形式）与TSIG固定的问题
        _在哪里SIG-validity-*域不会被正确，如果没有设置处理的32位体系结构固定的一个问题
          对每个区域部分。
        _略有改善的大日志文件重播时间
        _固定的几个小问题

    已知问题：
        _如果一个区的序列的方式被改变，它超越了一个值，如
          该杂志系列开始大于杂志连载结束，问题有望
          对于IXFR答案。
        _通知是在TCP忽略

20120709：
YADIFA1.0.1
_记录重复的压缩，现在是全球通过渠道，而不是

修正：
        _固定的一个问题，即glibc的断言对子级如果libgcc_s.so（libgcc_s.so.1）和libc.so（libc.so.6的），其中不
可YADIFA的chroot的目录内
_系统日志模块中固定的问题

已知问题：
_在32位架构中，SIG-validity-*字段不能正确地从<主>复制到<区>
作为一种变通方法，在32位架构设置SIG-有效性领域中的每个<区>集装箱

例如：
SIG-有效性间隔7
 SIG-有效性再生168
SIG-有效性抖动3600
_如果一个区的序列的方式被改变，它超越了一个值，如
该杂志系列开始大于杂志连载结束，问题有望
对于IXFR答案。
_通知是在TCP忽略

20120625：
YADIFA1.0.0
_ LTO支持，可以使用--enable-LTO启用但这不是正与铿锵。 LTO不增加
性能significally
_监听地址的并行处理现在可以启用。
它可以通过设置线程数按地址在<主>部分。
默认情况下YADIFA不会使用并行处理的这个功能一直没有
因为作为单一线程处理模型全面测试
_默认参数整定
_修复

已知的问题：
_在32位架构中，SIG-validity-*字段不能正确地从<主>复制到<区>
作为一种变通方法，在32位架构设置SIG-有效性领域中的每个<区>集装箱

例如：
SIG-有效性间隔7
 SIG-有效性再生168
SIG-有效性抖动3600

20120530：
YADIFA1.0.0RC3
_配置解析器现在忽略未定义的记录姓名和
有警告他们汇报
_ syslog消息，现在摆在“yadifad”的名称，而不是用于“系统日志”频道名称
_系统日志消息不打印从YADIFA的时候了
_提高参与加载本地缓存的从属区域的步骤
_区是在后台加载，现在
_手册页yadifad-conf.man5改名成yadifad.conf.man5

修正：
_ AXFR/ IXFR答案与RA置位的nolonger拒绝为无效
_ YADIFA现在回答再次SIGINT（关机）
_固定的一个问题，即过时的AXFR文件并不总是被删除
_固定时发生的IPv4和IPv6的可用来处理通知的问题
_固定重播期刊发行，其中一些RRSIGs记录没有正确删除
_固定的IPv6查询中出现的问题
_在一个特定的NSEC3错误答案的产生固定的问题
_固定命名查询式布局

已知的问题：
_如果一个区的序列的方式被改变，它超越了一个值，如
该杂志系列开始大于杂志连载结束，问题有望
对于IXFR答案。
_通知是在TCP忽略

20120328：
YADIFA1.0.0RC2
_工作文件创建错误日志修复问题
_固定在那里IXFR查询可能被拒绝是错误格式化的问题
_固定在查询记录文本的问题
_启用命令行选项（-u UID-g GID-d）

20120319：
YADIFA1.0.0RC1

是一个全功能的权威域名服务器：

- 工程为主要或次要名称服务器
- AXFR
- IXFR
- NOTIFY
- 的nsupdate
- TSIG
- 职业：
- IN
- CH（只是版本）
- 类型：
- AAAA
- CNAME
- DNSKEY
- DS
- HINFO
- MX
- NAPTR
- NS
- NSEC3
- NSEC3PARAM
- NSEC
- PTR
- RRSIG
- SOA
- SRV
- SSHFP
- TXT
- 自动辞职
- DNSSEC算法：
- 5（RSASHA1）
- 7（RSASHA1-NSEC3
- ACL的


已知问题：

NSEC3：_不能与多个NSEC3PARAM链混合OPT-IN/ OUT设置工作

_增加一个新的NSEC3链预计，主机发送NSEC3PARAM第一（它似乎并不总是如此）
我们那里的高手开始2上千NSEC3退出记录然后将600万NSEC3选择在记录，但并没有给NSEC3PARAM记录情况
第一。从服务器拒绝所有这些，因为它是无法将其链接到链。 （这其中有高优先级）

DNSSEC：_不允许改变区域安全模式（不安全，NSEC，NSEC3或）。一旦该区域被加载它保持它的安全模式。

_ NSEC和NSEC3记录的动态更新被拒绝

QUIT：在下列条件下，服务器将停机：

_检测的不可能的情况或内部诚信问题（即：以任何理由SOA已经从一个区域消失）

_达到内存限制，防止任何更多的工作

_ IPC问题，其中防止内部通信服务

ACL：_由于访问控制是由区而设置，CHAOS类不作为配置的区域，它是不可能的（还）特异性阻断CHAOS的查询。

20111121：
YADIFA0.5.5
- 许多修复

已知问题：NSEC3从属区域重播失败。

20110706：
YADIFA0.5.0
- 从模式，AXFR/ IXFR（无TSIG但对于从端传输）
- 回答一个来自主通知
- 大师名单投票（第一）主
- 保持.axfr＆.IX文件（删除废弃的）
- TSIG查询进行检查
- 区域负荷（日志）后重新播放区域的日志上启动
- 答案IXFR查询（日志）

20110601：
YADIFA0.4.0
操作：
- 它可以作为一个没有DNSSEC域名服务器
- 没有通知到从属名称服务器
- 守护
- 答案AXFR与TSIG查询
- 功能的nsupdate（日志）
- TSIG客户端服务器端将被传输，但不检查
- ACL作品
- 该区域有SOA，NS A资源记录。

20110524：
YADIFA0.3.0
首先发布在内部的yadifad20110524115500 GMT+1。

操作：
- 它可以作为一个没有DNSSEC域名服务器
- 没有通知到从属名称服务器
- 守护
- 答案AXFR查询
- 该区域有SOA，NS A资源记录。


20091224：
YADIFA0.2.0
_答案AXFR查询
_ ACL基于IP和TSIG（不是所有的查询类型ACL'ed尚）

20091104：
YADIFA0.1.0

YADIFA是一项正在进行的工作。其主要目标是对BIND或NSD替代。

版本0.1.0只是一个权威服务器。

它没有：
- AXFR/ IXFR功能
- dynupdate
- 为支持NSEC
- 对NSEC3的支持
- 缓存机制
- 额外的工具（eg.dig，dnssectools，钻，...）

它具有：
- 一个非常快速的方式给予权威解答
- 非常快速的方法加载数据库和检查区域文件

这第一个版本是有一种感觉它是如何工作的操作环境。

TODO

一切什么不落实，有落实。大部分代码是存在的，但是没有被激活。

没有适宜性测试已经完成。 （当然，这是在待办事项列表上）



Bug报告和邮件列表

        错误报告应送交

                bugreport@yadifa.eu
