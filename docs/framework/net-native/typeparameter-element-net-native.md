---
title: "&lt;TypeParameter&gt; 要素 (.NET ネイティブ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d37bb1b7-1ddc-4c6d-8ecf-583f804a2479
caps.latest.revision: 11
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 11
---
# &lt;TypeParameter&gt; 要素 (.NET ネイティブ)
メソッドに渡される型引数により表される型にポリシーを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Parameter Name="parameter_name"  
           Activate="policy_type"  
           Browse="policy_type"  
           Dynamic="policy_type"  
           Serialize="policy_type"  
           DataContractSerializer="policy_type"  
           DataContractJsonSerializer="policy_type"  
           XmlSerializer="policy_type"  
           MarshalObject="policy_type"  
           MarshalDelegate="policy_type"  
           MarshalStructure="policy_type" />  
  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|属性の型|説明|  
|---------------|--------------------|-----------------|  
|`Name`|全般|必須の属性です。 型のパラメーターの名前<xref:System.Type>します。 たとえば、メソッド シグネチャ `Type.GetInterfaceMap(Type interfaceType)` の場合、`Name` 属性の値は "interfaceType" です。|  
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
|*パラメーター名*|型のパラメーターの名前<xref:System.Type>します。 たとえば、メソッド シグネチャ `Type.GetInterfaceMap(Type interfaceType)` の場合、`Name` 属性の値は "interfaceType" です。|  
  
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
  
## <a name="remarks"></a>コメント  
 `<TypeParameter>`要素がに似ていますが、 [ <> \> ](../../../docs/framework/net-native/parameter-element-net-native.md)要素、型のパラメーターにのみその it を適用できる点が異なります<xref:System.Type>します。 これは、実行時に `Name` 属性により指定される型引数で表されるすべての型にポリシーを適用します。  
  
 たとえば、NewtonSoft の JSON シリアライザーには静的 `JsonConvert.DeserializeObject(String value, Type type)` メソッドが含まれています。 次のリフレクション ディレクティブは、  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Type Name="Newtonsoft.Json.JsonConvert" >  
      <Method Name="DeserializeObject">  
         <GenericParameter Name="type" Serialize="Required All" />  
      </Method>  
   </Type>  
</Directives>  
  
```  
  
 によって表されるランタイム型のメタデータが指定して、`type`引数利用できるようにシリアル化します。 これらのランタイム ディレクティブが次のソース コードを含むプロジェクトに適用された場合、  
  
```csharp  
  
Type t = typeof(StockQuote);  
Object obj = JsonConvert.DeserializeObject(data, t);  
  
```  
  
 リフレクション ディレクティブによって、`StockQuote` 型のメタデータが実行時に NewtonSoft の JSON シリアライザーで使用可能になります。  
  
## <a name="see-also"></a>関連項目  
 [<>\>要素](../../../docs/framework/net-native/method-element-net-native.md)   
 [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [ランタイム ディレクティブ ポリシーの設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)   
 [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)