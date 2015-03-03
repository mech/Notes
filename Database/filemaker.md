# FileMaker

* [Rfm community - Google Group](https://groups.google.com/forum/#!forum/rfmcommunity)
* [Fork of Rfm](https://github.com/ginjo/rfm)
* [Devise and Rfm?](http://stackoverflow.com/questions/16061134/devise-on-ginjo-rfm)
* [Official documentation](http://www.filemaker.com/support/product/documentation.html)

## External Storage

* [Storing container field data externally](http://help.filemaker.com/app/answers/detail/a_id/10244/~/storing-container-field-data-externally)
* [FileMaker 12 Managing Container Data](http://www.dbservices.com/articles/filemaker-12-managing-container-data)

## Custom Web Publishing with XML

    /fmi/xml/fmresultset.xml?-db=FMServer_Sample&-lay=Tasks&-findall=
    /fmi/xml/FMPXMLLAYOUT.xml?-db=FMServer_Sample&-lay=Tasks&-view

The `fmresultset` grammar consists of:

```
<fmresultset xmlns="http://www.filemaker.com/xml/fmresultset" version="1.0">
  <error code="0"/>
  
  <datasource total-count="100" />
  
  <metadata>
    <field-definition name="" />
    <relatedset-definition table="">
      <field-definition name="" />
    </relatedset-definition>
  </metadata>
  
  <resultset count="1">
  
    <record mod-id="0" record-id="1">
      <field name="Start Date">
        <data>03/06/2014</data>
      </field>
    </record>
  
  </resultset>
</fmresultset>
```

## Security

CWP(XML) enables you to restrict access to your published databases through:

* Password protection
* Database encryption (Only available for FileMaker Pro Advanced)
* Secure connections using SSL

If there is no Extended Privilege, you will see this error (if using Rfm):

    Rfm::AuthenticationError: The account name () or password provided is not correct (or the account doesn't have the fmxml extended privilege).
    
### Restrict local IP address

Apache config file is at:

    /Library/FileMaker Server/HTTPServer/conf/httpd.conf
    
## Performance

* [Solving performance emergencies with FileMaker Server](http://www.briandunning.com/browse/browse0110.shtml)

## Mac Pro Issues

* [502 Bad Gateway error with FM Server 13](http://forums.filemaker.com/posts/95047d15f3)
* [Brand new Mac Pro install of FM Server 13 always "Not Responding"](https://fmdev.filemaker.com/message/142858)
* [FM Forums - Encounter crash on new Mac Pro](http://fmforums.com/forum/topic/91513-encounter-crash-on-new-mac-pro-graphics-issues/)