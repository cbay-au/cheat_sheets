

	ref:-	https://highon.coffee/blog/subfinder-cheat-sheet/
	ref:-	https://docs.projectdiscovery.io/tools/subfinder/install#post-install-configuration


	Subfinder supports the following data API sources:

	NAME		URL
	BeVigil		https://bevigil.com/osint-api

	BinaryEdge	https://binaryedge.io

	BufferOver	https://tls.bufferover.run

	C99		https://api.c99.nl/

	Censys		https://censys.io

	CertSpotter	https://sslmate.com/certspotter/api/

	Chaos		https://chaos.projectdiscovery.io

	Chinaz		http://my.chinaz.com/ChinazAPI/DataCenter/MyDataApi

	DNSDB		https://api.dnsdb.info

	Fofa		https://fofa.info/static_pages/api_help

	FullHunt	https://fullhunt.io

	GitHub		https://github.com

	Intelx		https://intelx.io

	PassiveTotal	http://passivetotal.org

	quake		https://quake.360.cn

	Robtex		https://www.robtex.com/api/

	SecurityTrails	http://securitytrails.com

	Shodan		https://shodan.io

	ThreatBook	https://x.threatbook.cn/en

	VirusTotal	https://www.virustotal.com

	WhoisXML API	https://whoisxmlapi.com/

	ZoomEye		https://www.zoomeye.org

	ZoomEye API	https://api.zoomeye.org

	dnsrepo		https://dnsrepo.noc.org

	Hunter		https://hunter.qianxin.com/

	Facebook	https://developers.facebook.com

	BuiltWith	https://api.builtwith.com/domain-api




	Verify Subfinder Results With HTTPX
		Chain up other tools within your workflow, such as verifying targets have web servers using HTTPX:
			echo hackerone.com | subfinder -silent | httpx -silent

	Subfinder + Naabu Portscan
		echo hackerone.com | subfinder -silent | naabu -silent
