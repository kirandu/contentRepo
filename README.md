# contentRepo

Prerequisites: 
1) .Net Core 
 
Task:
Checkout following project from git 
https://github.com/kirandu/contentRepo 
 
Continue developing ContentController, it should serve following requirements
Content files are available under data folder
 
1.	Content controller should accept two parameters, 
1.	Path -> Path is relative path from data folder
2.	Depth -> Depth inside the data folder that is requested 
 
2.	Content controller when requested with proper path and depth, it should output content from files
 
3.	Content output format should be xml and json, depending on the content-type header
 
4.	Http request should have cachable caching-headers, Etag
 
5.	Unit tests
 
6.	Error handling
 
7.	Corner cases (as comments, as unit tests ...)
 
Samples1:
Input: https://localhost:5001/content?path=content.com
 
output:
```xml
<items>
               <item path="/content.com" language="en" version="1" parentid="{98518673-BC81-4F01-BD3A-4094574EF9BB}" id="{5AD576CB-BD7D-4901-9D00-D4485D115266}" template="site root" templateId="{3A55E9A3-F274-48E3-ADB1-DE196B323926}" key="m2.content.com" name="m2.content.com">
                              <fields>
                                            <field key="canonicaldomains" type="Bwin Name Value List Sorted">
                                                           <content>
                                                                          <bwinnamevalue>
                                                                                         <entry key="sports.m.content.com">*.sports.m.content.com</entry>
                                                                          </bwinnamevalue>
                                                           </content>
                                            </field>
                                            <field key="defaultpagetitle" type="Single-Line Text">
                                                           <content>
                                                                          <![CDATA[ bwin ]]>
                                                           </content>
                                            </field>
                              </fields>
               </item>
</items>
´´´
 
Samples2:
Input: https://localhost:5001/content?path=content.com&depth=1
 
output:
´´´xml
<items>
	<item path="/content.com" language="en" version="1" parentid="{98518673-BC81-4F01-BD3A-4094574EF9BB}"
        id="{5AD576CB-BD7D-4901-9D00-D4485D115266}"
        template="site root"
        templateId="{3A55E9A3-F274-48E3-ADB1-DE196B323926}"
        key="m2.content.com" name="m2.content.com">
		<fields>
			<field key="canonicaldomains" type="Bwin Name Value List Sorted">
				<content>
					<bwinnamevalue>
						<entry key="sports.m.content.com">*.sports.m.content.com</entry>
					</bwinnamevalue>
				</content>
			</field>
			<field key="defaultpagetitle" type="Single-Line Text">
				<content>
					<![CDATA[ bwin ]]>
				</content>
			</field>
		</fields>
		<item path="/content.com/playground-v1.0" language="en" version="1" parentid="{5AD576CB-BD7D-4901-9D00-D4485D115266}" id="{F368FA3B-0CB7-4FD6-AE0C-517729C14D63}" template="plugin root" templateId="{A262FCE6-16C3-4AC1-8719-5F36E07820EF}" key="playground-v1.0" name="Playground-v1.0">
			<fields>
				<field key="product" type="Checklist">
					<content>
/sitecore/templates/vanilla/framework/plugin root/basedata/product/vanillatestplugin
</content>
				</field>
				<field key="productcontact" type="Multi-Line Text">
					<content>
						<![CDATA[ owned by Vanilla Framework Team, Vienna ]]>
					</content>
				</field>
				<field key="technicalcontact" type="Multi-Line Text">
					<content>
						<![CDATA[ owned by Vanilla Framework Team, Vienna ]]>
					</content>
				</field>
			</fields>
		</item>
	</item>
</items>

´´´