---
title: '&lt;declaredTypes&gt; 要素の &lt;add&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- data contracts
- dataContractSerializer element
- DataContractSerializer
- DataContractAttribute
ms.assetid: c3d37ae4-8f1c-463f-b195-658c5a7e90a1
ms.openlocfilehash: 90eaf11ce8b9e3675a23ed3875680b03f149b56b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754120"
---
# <a name="ltaddgt-of-ltdeclaredtypesgt-element"></a>&lt;declaredTypes&gt; 要素の &lt;add&gt;
逆シリアル化中に、<xref:System.Runtime.Serialization.DataContractSerializer> で使用される型を追加します。 各宣言型は、宣言型のフィールドまたはプロパティとして返される既知の型を含みます。  
  
 system.runtime.serialization  
\<dataContractSerializer >  
\<declaredTypes >  
\<追加 > の\<declaredTypes >  
  
## <a name="syntax"></a>構文  
  
```xml  
<add type="String">  
   <knownType type="String">  
       <parameter index="Integer"  
                  type="String" />  
   </knownType>  
</add>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|型|必須の文字列属性です。<br /><br /> 型名 (名前空間を含む)、アセンブリ名、バージョン番号、カルチャ、および公開キー トークンを指定します。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|追加される宣言型の既知の型を指定します。 宣言型がジェネリック型の場合は、既知の型を返すために使用されるジェネリック パラメーターを指定するために、`<knownType>` にパラメーター要素も追加する必要があります。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/declaredtypes.md)|<xref:System.Runtime.Serialization.DataContractSerializer> による逆シリアル化中に既知のタイプを必要とするタイプが含まれています。|  
  
## <a name="remarks"></a>コメント  
 既知の型の詳細については、次を参照してください。[データ コントラクトの既知の型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)と<xref:System.Runtime.Serialization.DataContractSerializer>です。  
  
 参照してください、 [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)この要素の使用例についてはします。  
  
> [!NOTE]
>  <xref:System.Object> 型を `<declaredType>` として追加すると、<xref:System.Configuration.ConfigurationErrorsException> がスローされます。 これは、構成で <xref:System.Object> 型を宣言型として使用できないためです。  
  
## <a name="example"></a>例  
  
```xml  
<add type="MyCompany.Library.Shape,   
           MyAssembly, Version=2.0.0.0, Culture=neutral,  
           PublicKeyToken=XXXXXX, processorArchitecture=MSIL">  
           <knownType type="MyCompany.Library.Circle,   
                      MyAssembly, Version=2.0.0.0, Culture=neutral,  
                      PublicKeyToken=XXXXXX,  
                      processorArchitecture=MSIL"/>  
</add>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [既知のデータ コントラクト型](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [\<追加 > の\<declaredTypes >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
