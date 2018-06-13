---
title: '&lt;enforceFIPSPolicy&gt;要素'
ms.date: 03/30/2017
helpviewer_keywords:
- enforceFIPSPolicy element
- FIPS
- <enforceFIPSPolicy> element
- Federal Information Processing Standards (FIPS)
ms.assetid: c35509c4-35cf-43c0-bb47-75e4208aa24e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9040bf2548964cf6df5f4fd87ee9f6d979c7df1e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746216"
---
# <a name="ltenforcefipspolicygt-element"></a>&lt;enforceFIPSPolicy&gt;要素
暗号化アルゴリズムが連邦情報処理規格 (FIPS: Federal Information Processing Standard) に準拠する必要があるコンピューターの構成要件を強制するかどうかを指定します。  
  
 \<configuration > 要素  
\<ランタイム > 要素  
\<enforceFIPSPolicy > 要素  
  
## <a name="syntax"></a>構文  
  
```xml  
<enforceFIPSPolicy enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|enabled|必須の属性です。<br /><br /> 暗号化アルゴリズムは FIPS に準拠する必要があります、コンピューターの構成要件の適用を有効にするかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`true`|お使いのコンピューターが、FIPS 対応である暗号アルゴリズムを要求するように構成されている場合は、その要件が適用されます。 クラス コンス トラクターは、FIPS 準拠アルゴリズムを実装する場合または`Create`そのコンピューターで実行された場合、そのクラスのメソッドが例外をスローします。 既定値です。|  
|`false`|アプリケーションで使用される暗号アルゴリズムは、コンピューターの構成に関係なく、FIPS に準拠する必要はありません。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 以降、.NET Framework 2.0 では、暗号アルゴリズムを実装するクラスの作成は、コンピューターの構成によって制御されます。 FIPS に準拠するアルゴリズムを要求するように、コンピューターが構成されており、クラスが FIPS に準拠していないするアルゴリズムを実装する、そのクラスのインスタンスを作成しようとするとは、例外をスローします。 コンス トラクターをスロー、<xref:System.InvalidOperationException>例外、および`Create`メソッドをスロー、<xref:System.Reflection.TargetInvocationException>と内部例外<xref:System.InvalidOperationException>例外。  
  
 アプリケーションの構成が FIPS 準拠を必要とするコンピューターで実行して、アルゴリズムが FIPS に準拠していないが使用されて、アプリケーション、することができます要素を使用してこの構成ファイルで、共通言語ランタイム (CLR) を防ぐためにFIPS 準拠を適用します。 この要素で導入された、[!INCLUDE[net_v20SP1_long](../../../../../includes/net-v20sp1-long-md.md)]です。  
  
## <a name="example"></a>例  
 次の例では、CLR が FIPS 準拠を適用することを防止する方法を示します。  
  
```xml  
<configuration>  
    <runtime>  
        <enforceFIPSPolicy enabled="false"/>  
    </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [暗号モデル](../../../../../docs/standard/security/cryptography-model.md)
