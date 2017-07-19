---
title: "&lt;Type&gt; 要素 (.NET ネイティブ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e88d368-a886-4f1e-8eb6-6127979a9fce
caps.latest.revision: 33
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 33
---
# &lt;Type&gt; 要素 (.NET ネイティブ)
クラスや構造体などの特定の型に実行時ポリシーを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Type Name="type_name"  
      Activate="policy_type"  
      Browse="policy_type"  
      Dynamic="policy_type"  
      Serialize="policy_type"   
      DataContractSerializer="policy_setting"  
      DataContractJsonSerializer="policy_setting"  
      XmlSerializer="policy_setting"  
      MarshalObject="policy_setting"  
      MarshalDelegate="policy_setting"  
      MarshalStructure="policy_setting" />  
  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|属性の型|説明|  
|---------------|--------------------|-----------------|  
|`Name`|全般|必須の属性です。 型名を指定します。|  
|`Activate`|反射|省略可能な属性です。 コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。|  
|`Browse`|反射|省略可能な属性です。 プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。|  
|`Dynamic`|反射|省略可能な属性です。 コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。|  
|`Serialize`|シリアル化|省略可能な属性です。 コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。|  
|`DataContractSerializer`|シリアル化|省略可能な属性です。 使用するシリアル化のポリシーを制御、 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>クラスです。|  
|`DataContractJsonSerializer`|シリアル化|省略可能な属性です。 ポリシーを使用する JSON シリアル化を制御、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName>クラスです。|  
|`XmlSerializer`|シリアル化|省略可能な属性です。 使用する XML シリアル化のポリシーを制御、<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>クラスです。|  
|`MarshalObject`|Interop|省略可能な属性です。 Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。|  
|`MarshalDelegate`|Interop|省略可能な属性です。 ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。|  
|`MarshalStructure`|Interop|省略可能な属性です。 値型をネイティブ コードにマーシャリングするためのポリシーを制御します。|  
  
## <a name="name-attribute"></a>Name 属性  
  
|値|説明|  
|-----------|-----------------|  
|*type_name*|型名。 この場合`<Type>`要素のいずれかの子では、 [ <> \> ](../../../docs/framework/net-native/namespace-element-net-native.md)要素または別`<Type>`要素、 *type_name*名前空間なしの型の名前を含めることができます。 それ以外の場合、 *type_name*完全修飾型名を含める必要があります。|  
  
## <a name="all-other-attributes"></a>その他すべての属性  
  
|値|説明|  
|-----------|-----------------|  
|*policy_setting*|このポリシーの種類に適用する設定です。 指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。 詳細については、次を参照してください。[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/attributeimplies-element-net-native.md)|含んでいる型が属性の場合は、その属性が適用されるコード要素の実行時ポリシーを定義します。|  
|[<>\>](../../../docs/framework/net-native/event-element-net-native.md)|この型に属するイベントにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/field-element-net-native.md)|この型に属するフィールドにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|ジェネリック型のパラメーターの型にポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/impliestype-element-net-native.md)|型にポリシーを適用します (それを含む `<Type>` 要素により表される型にそのポリシーが適用されている場合)。|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|この型に属するメソッドにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|この型に属する構築されたジェネリック メソッドにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/property-element-net-native.md)|この型に属するプロパティにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/subtypes-element-net-native.md)|それを含む型から継承されたすべてのクラスに実行時ポリシーを適用します。|  
|`<Type>`|入れ子になった型にリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|構築されたジェネリック型にリフレクション ポリシーを適用します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/application-element-net-native.md)|実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。|  
|[<>\>](../../../docs/framework/net-native/assembly-element-net-native.md)|指定したアセンブリ内のすべての型にリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/library-element-net-native.md)|実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。|  
|[<>\>](../../../docs/framework/net-native/namespace-element-net-native.md)|名前空間内のすべての型にリフレクション ポリシーを適用します。|  
|`<Type>`|型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
  
## <a name="remarks"></a>コメント  
 リフレクション、シリアル化、および相互運用属性はすべて省略可能です。 いずれも存在しない場合、`<Type>` 要素は、その子型が個々のメンバーのポリシーを定義するコンテナーとして機能します。  
  
 場合、`<Type>`要素の子では、 [ <> \</> \> ](../../../docs/framework/net-native/assembly-element-net-native.md)、 [ <> \</> \> ](../../../docs/framework/net-native/namespace-element-net-native.md)、 `<Type>`、または[ <> \> ](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)要素、親要素によって定義されたポリシー設定をオーバーライドしています。  
  
 ジェネリック型の `<Type>` 要素は、独自のポリシーを持たないすべてのインスタンス化にそのポリシーを適用します。 によって構築されたジェネリック型のポリシーが定義されている、 [ <> \> ](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)要素。  
  
 アクサン グラーブ記号で名前を修飾する型がジェネリック型の場合は、(' ') のジェネリック パラメーターの番号を使用してその後にします。 たとえば、`Name`の属性、`<Type>`の要素、 <xref:System.Collections.Generic.List%601?displayProperty=fullName>クラスとして位置付け`Name="System.Collections.Generic.List`1"'。  
  
## <a name="example"></a>例  
 次の例では、リフレクションを使用して、フィールド、プロパティ、およびメソッドに関する情報を表示、 <xref:System.Collections.Generic.List%601?displayProperty=fullName>クラスです。 変数`b`の例では、 [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx)コントロールです。 この例は単に型情報を取得するのみであるため、メタデータの可用性は `Browse` ポリシー設定により制御されます。  
  
 [!code-csharp[ProjectN_Reflection#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/browsegenerictype1.cs#3)]  
  
 のメタデータ、<xref:System.Collections.Generic.List%601>クラスによって自動的に含め、[!INCLUDE[net_native](../../../includes/net-native-md.md)]実行時に指定されたメンバー情報を表示するツール チェーンでは、例では、失敗します。 必要なメタデータを提供するには、次の `<Type>` 要素をランタイム ディレクティブ ファイルに追加します。 親を指定しているため、注意してください。 [ <> \> ](../../../docs/framework/net-native/namespace-element-net-native.md)要素、で完全修飾型名を用意する必要はありません、`<Type>`要素。  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="*Application*" Dynamic="Required All" />  
      <Namespace Name ="System.Collections.Generic" >  
        <Type Name="List`1" Browse="Required All" />   
     </Namespace>  
   </Application>  
</Directives>  
  
```  
  
## <a name="example"></a>例  
 次の例では、リフレクションを使用して、取得、 <xref:System.Reflection.PropertyInfo>を表すオブジェクト、 <xref:System.String.Chars%2A?displayProperty=fullName>プロパティです。 次を使用して、 [PropertyInfo.GetValue (オブジェクトを使用してオブジェクト\<xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=fullName>メソッド、文字列の&7; 番目の文字の値を取得し、文字列のすべての文字を表示します。 変数`b`の例では、 [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx)コントロールです。  
  
 [!code-csharp[ProjectN_Reflection#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/propertyinfo1.cs#1)]  
  
 のメタデータ、<xref:System.String>オブジェクトが使用できないへの呼び出し、 [PropertyInfo.GetValue (Object, Object\<xref:System.Reflection.PropertyInfo.GetValue%28System.Object%2CSystem.Object%5B%5D%29?displayProperty=fullName>メソッドがスローされます、 <xref:System.NullReferenceException>実行時例外でコンパイルすると、[!INCLUDE[net_native](../../../includes/net-native-md.md)]ツール チェーン。 例外を排除し、必要なメタデータを提供するには、次の `<Type>` 要素をランタイム ディレクティブ ファイルに追加します。  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
    <Type Name="System.String" Dynamic="Required Public"/> -->  
  </Application>  
</Directives>  
  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [ランタイム ディレクティブ ポリシーの設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)