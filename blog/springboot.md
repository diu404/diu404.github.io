[![](../images/banner.png "首页")](https://diu404.github.io)

#### spingboot获取配置属性
eg:application.properties
```
author.str=测试
author.map0[k00]=v00
author.map0[k01]=v01
author.map1={\
   "k10":"v10"\
  ,"k11":"v11"\
  }
author.lst0[0]=lst00
author.lst0[1]=lst01
author.lst1=lst10,lst11
author.lst2=lst20,lst21
author.lst3=lst30,lst31
```
Author.java
```
@Component
@ConfigurationProperties("author")
@Getter
@Setter
@NoArgsConstructor
@AllArgsConstructor
@Builder
@ToString
public class Author {
    private String str;
    private Map<String,String> map0=new HashMap<>();
    private List<String> lst0=new ArrayList<>();
    private List<String> lst1=new ArrayList<>();
}
/
    @Value("#{${author.map1}}")
    private Map<String,String> map1;
    @Value("${author.lst2:}")
    private List<String> lst2;
    @Value("#{'${author.lst3}'.split('\\,',-1)}")
    private List<String> lst3;
```
