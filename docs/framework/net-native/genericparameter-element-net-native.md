---
title: "&lt;GenericParameter&gt; 要素 (.NET ネイティブ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cbd49732-3615-49a5-a900-f96947cdc3e6
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;GenericParameter&gt; 要素 (.NET ネイティブ)
ジェネリック型またはメソッドのパラメーターの型にポリシーを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<GenericParameter Name="generic_parameter_name"  
                  Activate="policy_type"  
                  Browse="policy_type"  
                  Dynamic="policy_type"  
                  Serialize="policy_type" />  
                  DataContractSerializer="policy_type"  
                  DataContractJsonSerializer="policy_type"  
                  XmlSerializer="policy_type"  
                  MarshalObject="policy_type"  
                  MarshalDelegate="policy_type"  
                  MarshalStructure="policy_type"  
  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|属性の型|説明|  
|---------------|--------------------|-----------------|  
|`Name`|全般|必須の属性です。 ジェネリック パラメーターの名前。 たとえば、ジェネリック デリゲート<xref:System.Func%603>の値、`Name`属性は"TResult"デリゲートの戻り値に実行時ポリシーを適用する\</T1, T2, TResult>。|  
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
|*generic_parameter_name*|必須の属性です。 ジェネリック型パラメーターの名前。 たとえば、ジェネリック デリゲート<xref:System.Func%603>、 *generic_parameter_name* "TResult"の値には、デリゲートの戻り値に実行時ポリシーが適用されます\</T1, T2, TResult>。|  
  
## <a name="all-other-attributes"></a>その他すべての属性  
  
|値|説明|  
|-----------|-----------------|  
|*policy_setting*|このポリシーの種類に適用する設定です。 指定できる値は、`All`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。 詳細については、次を参照してください。[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|コンストラクターまたはメソッドにランタイム リフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|クラスや構造体など、特定の型にランタイム リフレクション ポリシーを適用します。|  
  
## <a name="remarks"></a>コメント  
 `<GenericParameter>`要素のいずれかの子では、 [ <> \> ](../../../docs/framework/net-native/method-element-net-native.md)または[ <> \> ](../../../docs/framework/net-native/type-element-net-native.md)要素、ジェネリック型またはメソッド シグネチャでその名前で指定されている特定のジェネリック型パラメーターにポリシーを適用するために使用します。  
  
 `<GenericParameter>` 要素は、シリアライザーで使用する場合に最も役立ちます。 次の例では、`<GenericParameter>`型にポリシーを適用する要素`T`、NewtonSoft の JSON シリアライザーの呼び出しで[JsonConvert.DeserializeObject<>\>(String)](http://james.newtonking.com/json/help/index.html?topic=html/T_Newtonsoft_Json_JsonConvert.htm)メソッドのオーバー ロードします。  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject{T}">  
         <GenericParameter Name="T" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
  
```  
  
## <a name="see-also"></a>関連項目  
 [<>\>要素](../../../docs/framework/net-native/method-element-net-native.md)   
 [<>\>要素](../../../docs/framework/net-native/type-element-net-native.md)   
 [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [ランタイム ディレクティブ ポリシーの設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)   
 [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)