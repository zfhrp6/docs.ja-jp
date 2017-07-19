---
title: "&lt;Application&gt; 要素 (.NET ネイティブ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b4e9b37a-059b-4076-8f56-cb3f9cef0cd9
caps.latest.revision: 21
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 21
---
# &lt;Application&gt; 要素 (.NET ネイティブ)
実行時にリフレクションに使用可能なメタデータを持つアプリケーション全体の型と型のメンバーのコンテナーとして機能し、アプリ内のすべてのプログラム要素にランタイム リフレクション ポリシーを適用します。  
  
 <>\>要素  
<>\>要素 (rd.xml)  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Application Activate="policy_setting"  
             Browse="policy_setting"  
             Dynamic="policy_setting"  
             Serialize="policy_setting"  
             DataContractSerializer="policy_setting"  
             DataContractJsonSerializer="policy_setting"  
             XmlSerializer="policy_setting"  
             MarshalObject="policy_setting"  
             MarshalDelegate="policy_setting"  
             MarshalStructure="policy_setting" />  
  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。 「子要素」の表では、ポリシーは実行時に特定のプログラム要素で使用可能になるメタデータの種類を示します。  
  
### <a name="attributes"></a>属性  
  
|属性|属性の型|説明|  
|---------------|--------------------|-----------------|  
|`Activate`|反射|省略可能な属性です。 コンストラクターへの実行時アクセスを制御して、インスタンスのアクティブ化を有効にします。|  
|`Browse`|反射|省略可能な属性です。 型に関する情報の照会や型の列挙を制御しますが、実行時の動的アクセスは有効にしません。|  
|`Dynamic`|反射|省略可能な属性です。 コンストラクター、メソッド、フィールド、プロパティ、およびイベントを含むすべての型のメンバーへの実行時アクセスを制御して、動的プログラミングを有効にします。|  
|`Serialize`|シリアル化|省略可能な属性です。 コンストラクター、フィールド、およびプロパティへの実行時アクセスを制御し、Newtonsoft の JSON シリアライザーなどのライブラリによって型インスタンスをシリアル化および逆シリアル化できるようにします。|  
|`DataContractSerializer`|シリアル化|省略可能な属性です。 使用するシリアル化のポリシーを制御、 <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=fullName>クラスです。|  
|`DataContractJsonSerializer`|シリアル化|省略可能な属性です。 ポリシーを使用する JSON シリアル化を制御、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer?displayProperty=fullName>クラスです。|  
|`XmlSerializer`|シリアル化|省略可能な属性です。 使用する XML シリアル化のポリシーを制御、<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName>クラスです。|  
|`MarshalObject`|Interop|省略可能な属性です。 Windows ランタイムと COM に参照型をマーシャリングするためのポリシーを制御します。|  
|`MarshalDelegate`|Interop|省略可能な属性です。 ネイティブ コードへの関数ポインターとしてデリゲート型をマーシャリングするためのポリシーを制御します。|  
|`MarshalStructure`|Interop|省略可能な属性です。 ネイティブ コードに構造体をマーシャリングするためのポリシーを制御します。|  
  
## <a name="all-attributes"></a>すべての属性  
  
|値|説明|  
|-----------|-----------------|  
|*policy_setting*|アプリで型に適用する、このポリシーの設定です。 指定できる値は、`All`、`Auto`、`Excluded`、`Public`、`PublicAndInternal`、`Required Public`、`Required PublicAndInternal`、および `Required All` です。 詳細については、次を参照してください。[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/assembly-element-net-native.md)|特定のアセンブリ内のすべての型にポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/namespace-element-net-native.md)|特定の名前空間内のすべての型にポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|クラスや構造体などの特定の型にポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|構築されたジェネリック型にポリシーを適用します。 たとえば、 [ <> \> ](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)ポリシーを定義する要素を使用、`List<String>`型です。|  
|[<>\>](../../../docs/framework/net-native/method-element-net-native.md)|特定の型のメソッドにポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)|構築されたジェネリック メソッドにポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/property-element-net-native.md)|特定の型のプロパティにポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/field-element-net-native.md)|特定の型のフィールドにポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/event-element-net-native.md)|特定の型のイベントにポリシーを適用します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/directives-element-net-native.md)|ランタイム ディレクティブ ファイルのルート要素です。|  
  
## <a name="remarks"></a>コメント  
 [ <> \> ](../../../docs/framework/net-native/directives-element-net-native.md)&0; または&1; 個の要素を含めることができます`<Application>`要素。 1 つのリフレクション ディレクティブ ファイルに複数の `<Application>` 要素を含めることはサポートされていません。  
  
 `<Application>` 要素は、次の&2; とおりの方法で使用できます。  
  
-   実行時に必要なメタデータを持つプログラム要素を定義するためのコンテナーとして。 この場合、`<Application>` 要素に属性は必要ありません。 コンパイル時に、コンパイラ ツールは、.NET Framework コア ライブラリを含むすべてのライブラリで、`<Application>` 要素の子要素により示されるプログラム要素を検索します。 これに対し、コンパイラ ツールはにより指定されたライブラリのみを検索、 [ <> \> ](../../../docs/framework/net-native/library-element-net-native.md)要素の子要素により示されるプログラム要素[ <> \</> \>](../../../docs/framework/net-native/library-element-net-native.md)します。  
  
-   リフレクション、シリアル化、および相互運用に関するアプリケーション全体のポリシーを設定する要素として。 属性、`<Application>`要素により定義される子要素によってオーバーライドできますアプリケーション全体のポリシーを定義する、`<Application>`または[ <> \> ](../../../docs/framework/net-native/library-element-net-native.md)要素。  
  
## <a name="see-also"></a>関連項目  
 [<>\>要素](../../../docs/framework/net-native/library-element-net-native.md)   
 [<>\>要素](../../../docs/framework/net-native/directives-element-net-native.md)   
 [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)