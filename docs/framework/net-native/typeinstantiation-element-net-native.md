---
title: "&lt;TypeInstantiation&gt; 要素 (.NET ネイティブ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a5eada64-075b-4162-9655-ded84e4681f2
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;TypeInstantiation&gt; 要素 (.NET ネイティブ)
構築されたジェネリック型にランタイム リフレクション ポリシーを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<TypeInstantiation Name="type_name"  
                   Arguments="type_arguments"  
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
|`Arguments`|全般|必須の属性です。 ジェネリック型の引数を指定します。 複数の引数が存在する場合は、コンマで区切られます。|  
|`Activate`|反射|省略可能な属性です。 コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。|  
|`Browse`|反射|省略可能な属性です。 プログラム要素に関する情報の照会を制御しますが、実行時アクセスは有効にしません。|  
|`Dynamic`|反射|省略可能な属性です。 コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。|  
|`Serialize`|シリアル化|省略可能な属性です。 コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。|  
|`DataContractSerializer`|シリアル化|省略可能な属性です。 使用するシリアル化のポリシーを制御、 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>クラスです。|  
|`DataContractJsonSerializer`|シリアル化|省略可能な属性です。 ポリシーを使用する JSON シリアル化を制御、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName>クラスです。|  
|`XmlSerializer`|シリアル化|省略可能な属性です。 使用する XML シリアル化のポリシーを制御、<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>クラスです。|  
|`MarshalObject`|Interop|省略可能な属性です。 Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。|  
|`MarshalDelegate`|Interop|省略可能な属性です。 ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。|  
|`MarshalStructure`|Interop|省略可能な属性です。 ネイティブ コードに構造体をマーシャリングするためのポリシーを制御します。|  
  
## <a name="name-attribute"></a>Name 属性  
  
|値|説明|  
|-----------|-----------------|  
|*type_name*|型名。 この場合`<TypeInstantiation>`要素の子では、 [ <> \> ](../../../docs/framework/net-native/namespace-element-net-native.md)要素、 [ <> \> ](../../../docs/framework/net-native/type-element-net-native.md)要素、または別`<TypeInstantiation>`要素、 *type_name* 、名前空間なしで型の名前を指定できます。 それ以外の場合、 *type_name*完全修飾型名を含める必要があります。 型名は修飾されません。 たとえば、 <xref:System.Collections.Generic.List%601?displayProperty=fullName>オブジェクト、`<TypeInstantiation>`要素は次のように表示される可能性があります。<br /><br /> `\<TypeInstantiation Name=System.Collections.Generic.List Dynamic="Required Public" />`|  
  
## <a name="arguments-attribute"></a>引数属性  
  
|値|説明|  
|-----------|-----------------|  
|*type_argument*|ジェネリック型の引数を指定します。 複数の引数が存在する場合は、コンマで区切られます。 各引数は、完全修飾型名で構成されている必要があります。|  
  
## <a name="all-other-attributes"></a>その他すべての属性  
  
|値|説明|  
|-----------|-----------------|  
|*policy_setting*|構築されたジェネリック型のこのポリシーの種類に適用する設定です。 指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。 詳細については、次を参照してください。[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/event-element-net-native.md)|この型に属するイベントにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/field-element-net-native.md)|この型に属するフィールドにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/impliestype-element-net-native.md)|型にポリシーを適用します (それを含む `<TypeInstantiation>` 要素により表される型にそのポリシーが適用されている場合)。|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|この型に属するメソッドにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|この型に属する構築されたジェネリック メソッドにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/property-element-net-native.md)|この型に属するプロパティにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|入れ子になった型にリフレクション ポリシーを適用します。|  
|`<TypeInstantiation>`|入れ子になった構築されたジェネリック型にリフレクション ポリシーを適用します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/application-element-net-native.md)|実行時にリフレクションで使用可能なメタデータを持つ、アプリケーション全体の型と型のメンバーのコンテナーとして機能します。|  
|[<>\>](../../../docs/framework/net-native/assembly-element-net-native.md)|指定したアセンブリ内のすべての型にリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/library-element-net-native.md)|実行時にリフレクションに使用可能なメタデータを持つ型と型のメンバーを含むアセンブリを定義します。|  
|[<>\>](../../../docs/framework/net-native/namespace-element-net-native.md)|名前空間内のすべての型にリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
|`<TypeInstantiation>`|構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
  
## <a name="remarks"></a>コメント  
 リフレクション、シリアル化、および相互運用属性はすべて省略可能です。 ただし、そのうち少なくとも&1; つが存在する必要があります。  
  
 場合、`<TypeInstantiation>`要素の子では、 [ <> \</> \> ](../../../docs/framework/net-native/assembly-element-net-native.md)、 [ <> \</> \> ](../../../docs/framework/net-native/namespace-element-net-native.md)、または[ <> \</> \> ](../../../docs/framework/net-native/type-element-net-native.md)、要素、親要素によって定義されたポリシー設定をオーバーライドしています。 場合、 [ <> \> ](../../../docs/framework/net-native/type-element-net-native.md)要素は、対応するジェネリック型定義を定義、`<TypeInstantiation>`要素は指定の構築されたジェネリック型のインスタンス化についてのみランタイム リフレクション ポリシーをオーバーライドします。  
  
## <a name="example"></a>例  
 次の例では、リフレクションを使用して、構築されたジェネリック型定義を取得<xref:System.Collections.Generic.Dictionary%602>オブジェクト</TKey, TValue>。 情報を表示するリフレクションを使用<xref:System.Type>構築されたジェネリック型とジェネリック型定義を表すオブジェクト。 変数`b`の例では、 [TextBlock](http://msdn.microsoft.com/library/windows/apps/windows.ui.xaml.controls.textblock.aspx)コントロールです。  
  
 [!code-csharp[ProjectN_Reflection#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/makegenerictype1.cs#2)]  
  
 コンパイルされる、[!INCLUDE[net_native](../../../includes/net-native-md.md)]ツール チェーンの例では、スロー、 [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md)を呼び出す行を例外、 <xref:System.Type.GetGenericTypeDefinition%2A?displayProperty=fullName>メソッドです。 次の `<TypeInstantiation>` 要素をランタイム ディレクティブ ファイルに追加すると、この例外を排除して、必要なメタデータを提供できます。  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
    <Assembly Name="*Application*" Dynamic="Required All" />  
     <TypeInstantiation Name="System.Collections.Generic.Dictionary"  
                        Arguments="System.String,GenericType.Example"  
                        Dynamic="Required Public" />  
  </Application>  
</Directives>  
  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [ランタイム ディレクティブ ポリシーの設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)