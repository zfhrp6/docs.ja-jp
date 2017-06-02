---
title: "&lt;Method&gt; 要素 (.NET ネイティブ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 348b49e5-589d-4eb2-a597-d6ff60ab52d1
caps.latest.revision: 22
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 22
---
# &lt;Method&gt; 要素 (.NET ネイティブ)
コンストラクターまたはメソッドにランタイム リフレクション ポリシーを適用します。  
  
## <a name="syntax"></a>構文  
  
```xml  
  
<Method Name="method_name"  
        Signature="method_signature"  
        Browse="policy_type"  
        Dynamic="policy_type" />  
  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|属性の型|説明|  
|---------------|--------------------|-----------------|  
|`Name`|全般|必須の属性です。 メソッド名を指定します。|  
|`Signature`|全般|省略可能な属性です。 メソッド シグネチャを指定します。 複数のパラメーターが存在する場合はコンマで区切られます。 たとえば、次`<Method>`要素のポリシーを定義、 <xref:System.DateTimeOffset.ToString%28System.String%2CSystem.IFormatProvider%29>メソッドです。<br /><br /> `<Type Name="System.DateTime">    <Method Name="ToString" Signature="System.String,System.IFormatProvider"            Dynamic="Required" /> </Type>`<br /><br /> 属性が存在しない場合、ランタイム ディレクティブは、メソッドのすべてのオーバーロードに適用されます。|  
|`Browse`|反射|省略可能な属性です。 メソッドに関する情報の照会やメソッドの列挙を制御しますが、実行時の動的呼び出しは有効にしません。|  
|`Dynamic`|反射|省略可能な属性です。 コンストラクターまたはメソッドへの実行時アクセスを制御して、動的プログラミングを有効にします。 このポリシーにより、実行時にメンバーを動的に呼び出すことができます。|  
  
## <a name="name-attribute"></a>Name 属性  
  
|値|説明|  
|-----------|-----------------|  
|*メソッド名が*|メソッド名。 メソッドの型が、親によって定義された[ <> \> ](../../../docs/framework/net-native/type-element-net-native.md)または[ <> \> ](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)要素。|  
  
## <a name="signature-attribute"></a>シグネチャ属性  
  
|値|説明|  
|-----------|-----------------|  
|*method_signature*|メソッド シグネチャを形成するパラメーター型です。 複数のパラメーターは、`"System.String,System.Int32,System.Int32)"` のようにコンマで区切ります。 パラメーターの型名は完全修飾されている必要があります。|  
  
## <a name="all-other-attributes"></a>その他すべての属性  
  
|値|説明|  
|-----------|-----------------|  
|*policy_setting*|このポリシーの種類に適用する設定です。 指定できる値は、`Auto`、`Excluded`、`Included`、および `Required` です。 詳細については、次を参照してください。[ランタイム ディレクティブのポリシー設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/parameter-element-net-native.md)|メソッドに渡された引数の型にポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/genericparameter-element-net-native.md)|ジェネリック型またはメソッドのパラメーターの型にポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/impliestype-element-net-native.md)|型にポリシーを適用します (含んでいる `<Method>` 要素によって表されるメソッドにそのポリシーが適用されている場合)。|  
|[<>\>](../../../docs/framework/net-native/typeparameter-element-net-native.md)|によって表される型にポリシーを適用、<xref:System.Type>メソッドに渡される引数。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[<>\>](../../../docs/framework/net-native/type-element-net-native.md)|型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
|[<>\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md)|構築されたジェネリック型とそのすべてのメンバーにリフレクション ポリシーを適用します。|  
  
## <a name="remarks"></a>コメント  
 ジェネリック メソッドの `<Method>` 要素は、独自のポリシーを持たないインスタンス化すべてにそのポリシーを適用します。  
  
 `Signature` 属性を使用して、特定のメソッド オーバーロードのポリシーを指定できます。 そうしない場合、`Signature` 属性が存在しないと、メソッドのすべてのオーバーロードにランタイム ディレクティブが適用されます。  
  
 `<Method>` 要素を使用してコンストラクターのランタイム リフレクション ポリシーを定義することはできません。 Instead, use the `Activate` attribute of the  [<>\>](../../../docs/framework/net-native/assembly-element-net-native.md), [<>\>](../../../docs/framework/net-native/namespace-element-net-native.md), [<>\>](../../../docs/framework/net-native/type-element-net-native.md), or [<>\>](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) element.  
  
## <a name="example"></a>例  
 次の例の `Stringify` メソッドは、リフレクションを使用してオブジェクトを文字列形式に変換する汎用書式設定メソッドです。 オブジェクトの既定の呼び出しだけでなく`ToString`方法、メソッドでは、書式設定された結果文字列、オブジェクトを渡すことによって`ToString`メソッドに書式文字列、 <xref:System.IFormatProvider>実装、またはその両方です。 いずれかが呼び出すことも、 <xref:System.Convert.ToString%2A?displayProperty=fullName>バイナリ、16 進数、または&8; 進数形式に数値を変換するオーバー ロードします。  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 `Stringify` メソッドは、次のようなコードによって呼び出すことができます。  
  
 [!code-csharp[ProjectN_Reflection#7](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn_reflection/cs/method1.cs#7)]  
  
 ただし、.NET ネイティブでコンパイルしたときに例をスローできます例外の数、実行時に含む<xref:System.NullReferenceException>と[MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)例外を除き、これが発生したため、`Stringify`メソッドは、主に、.NET Framework クラス ライブラリでプリミティブ型を動的に書式設定をサポートします。 ただし、既定のディレクティブ ファイルではそのメタデータを使用できません。 そのメタデータが使用可能になる場合でも、例では、スロー [MissingRuntimeArtifactException](../../../docs/framework/net-native/missingruntimeartifactexception-class-net-native.md)例外のため、適切な`ToString`実装がネイティブ コードに含まれていません。  
  
 これらの例外をすべて使用して、除去できる、 [ <> \> ](../../../docs/framework/net-native/type-element-net-native.md)存在し、追加することでメタデータを持つ必要があります型を定義する要素`<Method>`メソッドの実装がオーバー ロードに、要素が動的に呼び出せるも存在します。 これらの例外を排除し、例をエラーなしで実行できるようにした default.rd.xml ファイルを次に示します。  
  
```xml  
  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <Assembly Name="*Application*" Dynamic="Required All" />  
  
     <Type Name = "System.Convert" Browse="Required Public" Dynamic="Required Public" >  
        <Method Name="ToString"    Dynamic ="Required" />  
     </Type>  
     <Type Name="System.Double" Browse="Required Public">  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int32" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Type Name ="System.Int64" Browse="Required Public" >  
        <Method Name="ToString" Dynamic="Required" />  
     </Type>  
     <Namespace Name="System" >  
        <Type Name="Byte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="DateTime" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Decimal" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Guid" Browse ="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Int16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="SByte" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="Single" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="TimeSpan" Browse="Required Public" >  
          <Method Name="ToString" Dynamic="Required" />           
        </Type>  
        <Type Name="UInt16" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt32" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
        <Type Name="UInt64" Browse="Required Public" >  
           <Method Name="ToString" Dynamic="Required" />  
        </Type>  
     </Namespace>  
  </Application>  
</Directives>  
  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム ディレクティブ (rd.xml) 構成ファイル リファレンス](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)   
 [ランタイム ディレクティブ要素](../../../docs/framework/net-native/runtime-directive-elements.md)   
 [ランタイム ディレクティブ ポリシーの設定](../../../docs/framework/net-native/runtime-directive-policy-settings.md)   
 [<>\>要素](../../../docs/framework/net-native/methodinstantiation-element-net-native.md)