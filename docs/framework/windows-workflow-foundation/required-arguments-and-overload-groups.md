---
title: "必須の引数とオーバーロード グループ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4ca3ed06-b9af-4b85-8b70-88c2186aefa3
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 必須の引数とオーバーロード グループ
アクティビティは、アクティビティの実行を有効にするためには特定の引数をバインドする必要があるように構成できます。`RequiredArgument` 属性は、アクティビティの特定の引数が必須であることを示す場合に使用します。また、`OverloadGroup` 属性は、必須の引数のカテゴリをグループ化する場合に使用します。これらの属性を使用することで、アクティビティ作成者は、単純なアクティビティ検証の構成も複雑な構成も適用できます。  
  
## 必須の引数の使用  
 アクティビティで `RequiredArgument` 属性を使用するためには、<xref:System.Activities.RequiredArgumentAttribute> を使用して目的の引数を指定します。次の例では、2 つの必須引数がある `Add` アクティビティが定義されています。  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 また、XAML では、必須引数の指定に <xref:System.Activities.RequiredArgumentAttribute> も使用されます。この例では、3 つの引数を使用して `Add` アクティビティを定義し、<xref:System.Activities.Statements.Assign%601> アクティビティを使用して追加操作を実行します。  
  
```xaml  
<Activity x:Class="ValidationDemo.Add" ...>  
  <x:Members>  
    <x:Property Name="Operand1" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Operand2" Type="InArgument(x:Int32)">  
      <x:Property.Attributes>  
        <RequiredArgumentAttribute />  
      </x:Property.Attributes>  
    </x:Property>  
    <x:Property Name="Result" Type="OutArgument(x:Int32)" />  
  </x:Members>  
  <Assign>  
    <Assign.To>  
      <OutArgument x:TypeArguments="x:Int32">[Result]</OutArgument>  
    </Assign.To>  
    <Assign.Value>  
      <InArgument x:TypeArguments="x:Int32">[Operand1 + Operand2]</InArgument>  
    </Assign.Value>  
  </Assign>  
</Activity>  
```  
  
 アクティビティが使用され、いずれかの必須引数がバインドされていない場合は、次の検証エラーが返されます。  
  
 **"Value for a required activity argument 'Operand1' was not supplied."**   
> [!NOTE]
>  検証のエラーと警告の確認方法と処理方法[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[アクティビティ検証の呼び出し](../../../docs/framework/windows-workflow-foundation//invoking-activity-validation.md)」を参照してください。  
  
## オーバーロード グループの使用  
 オーバーロード グループには、あるアクティビティ内で有効である引数の組み合わせを示すメソッドが用意されています。引数は <xref:System.Activities.OverloadGroupAttribute> を使用してグループ化されます。各グループには、<xref:System.Activities.OverloadGroupAttribute> によって指定される名前が与えられます。アクティビティが有効なのは、オーバーロード グループに含まれる 1 つの引数セットのみがバインドされる場合です。次の例では、[OverloadGroups](../../../docs/framework/windows-workflow-foundation/samples/overloadgroups.md) サンプルから取られた、`CreateLocation` クラスが定義されます。  
  
```csharp  
class CreateLocation: Activity  
{  
    [RequiredArgument]  
    public InArgument<string> Name { get; set; }  
  
    public InArgument<string> Description { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Latitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G1")]  
    public InArgument<int> Longitude { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    [OverloadGroup("G3")]  
    public InArgument<string> Street { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> City { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G2")]  
    public InArgument<string> State { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("G3")]  
    public InArgument<int> Zip { get; set; }                  
}  
```  
  
 このアクティビティの目的は、米国内の場所を指定することです。これを行うために、アクティビティのユーザーは、3 つある引数グループの 1 つを使用して場所を指定できます。引数の有効な組み合わせを指定するため、3 種類のオーバーロード グループを定義します。`G1` には `Latitude` および `Longitude` の引数が含まれます。`G2` には `Street`、`City`、および `State` が含まれます。`G3` には `Street` および `Zip` が含まれます。`Name` も必要な引数ですが、オーバーロード グループの一部ではありません。このアクティビティを有効にするには、1 つのオーバーロード グループのみから、すべての引数をバインドすると共に、`Name` をバインドする必要があります。  
  
 [データベース アクセス アクティビティ](../../../docs/framework/windows-workflow-foundation/samples/database-access-activities.md) サンプルから取得された次の例では、2 個のオーバーロード グループ `ConnectionString` および `ConfigFileSectionName` があります。このアクティビティを有効にするには、`ProviderName` および `ConnectionString` の引数がバインドされるか、`ConfigName` の引数がバインドされる必要がありますが、両方同時にバインドすることはできません。  
  
```  
Public class DbUpdate: AsyncCodeActivity  
{  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DefaultValue(null)]  
    public InArgument<string> ProviderName { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConnectionString")]  
    [DependsOn("ProviderName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConnectionString { get; set; }  
  
    [RequiredArgument]  
    [OverloadGroup("ConfigFileSectionName")]  
    [DefaultValue(null)]  
    public InArgument<string> ConfigName { get; set; }  
  
    [DefaultValue(null)]  
    public CommandType CommandType { get; set; }  
  
    [RequiredArgument]  
    public InArgument<string> Sql { get; set; }  
  
    [DependsOn("Sql")]  
    [DefaultValue(null)]  
    public IDictionary<string, Argument> Parameters { get; }  
  
    [DependsOn("Parameters")]  
    public OutArgument<int> AffectedRecords { get; set; }       
}  
```  
  
 オーバーロード グループを定義する場合:  
  
-   オーバーロード グループを別のオーバーロード グループのサブセットまたは等価セットにすることはできません。  
  
    > [!NOTE]
    >  この規則には例外が 1 つあります。オーバーロード グループが別のオーバーロード グループのサブセットであり、サブセットに `RequiredArgument` が `false` である引数のみが含まれている場合、オーバーロード グループは有効です。  
  
-   複数のオーバーロード グループは重なることはできます。しかし、一方か両方のオーバーロード グループの必須引数すべてがグループの積集合に含まれると、エラーになります。前の例では `G2` および `G3` のオーバーロード グループはオーバーラップしましたが、共通部分には一方または両方のグループの引数すべてが含まれてはいなかったため有効でした。  
  
 オーバーロード グループの引数をバインドする場合:  
  
-   オーバーロード グループ内の `RequiredArgument` 引数すべてがバインドされている場合、そのグループはバインドされていると見なされます。  
  
-   グループに `RequiredArgument` 引数がなく、1 つ以上の引数がバインドされている場合、そのグループはバインドされていると見なされます。  
  
-   複数あるオーバーロード グループのうち、1 つもバインドされていない場合は、検証エラーになります。ただし、1 つのオーバーロード グループに `RequiredArgument` 引数が 1 つもない場合を除きます。  
  
-   複数のオーバーロード グループをバインドすると、エラーになります。つまり、1 つのオーバーロード グループの必須引数すべてがバインドされ、かつ別のオーバーロード グループの任意の引数もバインドされると、エラーになります。