---
layout: page
title: "Q193080: HOWTO: Determine Operating System Regional Setting Language ID"
permalink: /kb/193/Q193080/
---

## Q193080: HOWTO: Determine Operating System Regional Setting Language ID

{% raw %}

	Article: Q193080
	Product(s): Microsoft FoxPro
	Version(s): 3.0,3.0b,5.0,5.0a,6.0
	Operating System(s): 
	Keyword(s): 
	Last Modified: 09-AUG-2001
	
	-------------------------------------------------------------------------------
	The information in this article applies to:
	
	- Microsoft Visual FoxPro for Windows, versions 3.0, 3.0b, 5.0, 5.0a, 6.0 
	-------------------------------------------------------------------------------
	
	SUMMARY
	=======
	
	The operating system's user-defined language identifier can be set using the
	Regional Settings option in the Control Panel. Some applications may need to
	determine which language ID the operating system is currently using. This
	article describes how to use the GetUserDefaultLCID API to determine this
	information.
	
	MORE INFORMATION
	================
	
	NOTE: The following code is case sensitive.
	
	This code displays the operating system's current language ID:
	
	     *!*      List All Supported Languages and Their ID's
	
	     *!*      Arabic (Saudi Arabia)                1025
	     *!*      Arabic (Iraq)                        2049
	     *!*      Arabic (Egypt)                       3073
	     *!*      Arabic (Libya)                       4097
	     *!*      Arabic (Algeria)                     5121
	     *!*      Arabic (Morocco)                     6145
	     *!*      Arabic (Tunisia)                     7169
	     *!*      Arabic (Oman)                        8193
	     *!*      Arabic (Yemen)                       9217
	     *!*      Arabic (Syria)                      10241
	     *!*      Arabic (Jordan)                     11265
	     *!*      Arabic (Lebanon)                    12289
	     *!*      Arabic (Kuwait)                     13313
	     *!*      Arabic (U.A.E.)                     14337
	     *!*      Arabic (Bahrain)                    15361
	     *!*      Arabic (Qatar)                      16385
	     *!*      Bulgarian                            1026
	     *!*      Catalan                              1027
	     *!*      Chinese (Taiwan)                     1028
	     *!*      Chinese (PRC)                        2052
	     *!*      Chinese (Hong Kong SAR               3076
	     *!*      Chinese (Singapore)                  4100
	     *!*      Czech                                1029
	     *!*      Danish                               1030
	     *!*      German (Standard)                    1031
	     *!*      German (Swiss)                       2055
	     *!*      German (Austrian)                    3079
	     *!*      German (Luxembourg)                  4103
	     *!*      German (Liechtenstein)               5127
	     *!*      Greek                                1032
	     *!*      English (United States)              1033
	     *!*      English (United Kingdom)             2057
	     *!*      English (Australian)                 3081
	     *!*      English (Canadian)                   4105
	     *!*      English (New Zealand)                5129
	     *!*      English (Ireland)                    6153
	     *!*      English (South Africa)               7177
	     *!*      English (Jamaica)                    8201
	     *!*      English (Caribbean)                  9225
	     *!*      English (Belize)                    10249
	     *!*      English (Trinidad)                  11273
	     *!*      Spanish (Traditional Sort)           1034
	     *!*      Spanish (Mexican)                    2058
	     *!*      Spanish (Modern Sort)                3082
	     *!*      Spanish (Guatemala)                  4106
	     *!*      Spanish (Costa Rica)                 5130
	     *!*      Spanish (Panama)                     6154
	     *!*      Spanish (Dominican Republic)         7178
	     *!*      Spanish (Venezuela)                  8202
	     *!*      Spanish (Colombia)                   9226
	     *!*      Spanish (Peru)                      10250
	     *!*      Spanish (Argentina)                 11274
	     *!*      Spanish (Ecuador)                   12298
	     *!*      Spanish (Chile)                     13322
	     *!*      Spanish (Uruguay)                   14346
	     *!*      Spanish (Paraguay)                  15370
	     *!*      Spanish (Bolivia)                   16394
	     *!*      Spanish (El Salvador)               17418
	     *!*      Spanish (Honduras)                  18442
	     *!*      Spanish (Nicaragua)                 19466
	     *!*      Spanish (Puerto Rico)               20490
	     *!*      Finnish                              1035
	     *!*      French (Standard)                    1036
	     *!*      French (Belgian)                     2060
	     *!*      French (Canadian)                    3084
	     *!*      French (Swiss)                       4108
	     *!*      French (Luxembourg)                  5132
	     *!*      Hebrew                               1037
	     *!*      Hungarian                            1038
	     *!*      Icelandic                            1039
	     *!*      Italian (Standard)                   1040
	     *!*      Italian (Swiss)                      2064
	     *!*      Japanese                             1041
	     *!*      Korean                               1042
	     *!*      Korean (Johab)                       2066
	     *!*      Dutch (Standard)                     1043
	     *!*      Dutch (Belgian)                      2067
	     *!*      Norwegian (Bokmal)                   1044
	     *!*      Norwegian (Nynorsk)                  2068
	     *!*      Polish                               1045
	     *!*      Portuguese (Brazil)                  1046
	     *!*      Portuguese (Portugal)                2070
	     *!*      Romanian                             1048
	     *!*      Russian                              1049
	     *!*      Croatian                             1050
	     *!*      Serbian (Latin)                      2074
	     *!*      Serbian (Cyrillic)                   3098
	     *!*      Slovak                               1051
	     *!*      Albanian                             1052
	     *!*      Swedish                              1053
	     *!*      Swedish (Finland)                    2077
	     *!*      Thai                                 1054
	     *!*      Turkish                              1055
	     *!*      Indonesian                           1057
	     *!*      Ukrainian                            1058
	     *!*      Belarusian                           1059
	     *!*      Slovenian                            1060
	     *!*      Estonian                             1061
	     *!*      Latvian                              1062
	     *!*      Lithuanian                           1063
	     *!*      Farsi                                1065
	     *!*      Vietnamese                           1066
	     *!*      Basque                               1069
	     *!*      Afrikaans                            1078
	     *!*      Faeroese                             1080
	
	     *!*      Declare GetUserDefaultLCID API Function
	
	     DECLARE LONG GetUserDefaultLCID IN WIN32API
	
	     *!*      Get Language ID *****
	
	     ?GetUserDefaultLCID()
	
	Additional query words: kbVFp600 kbVFp300 kbVFp300b kbVFp500 kbVFp500a kbAPI
	
	======================================================================
	Keywords          :  
	Technology        : kbVFPsearch kbAudDeveloper kbVFP300 kbVFP300b kbVFP500 kbVFP600 kbVFP500a
	Version           : :3.0,3.0b,5.0,5.0a,6.0
	Issue type        : kbhowto
	
	=============================================================================
	

{% endraw %}
