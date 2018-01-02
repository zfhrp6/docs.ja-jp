---
title: "&lt;developmentMode&gt;要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a77f93a0dff198821509c2c26f67caa137073ced
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltdevelopmentmodegt-element"></a>&lt;developmentMode&gt;要素
DEVPATH 環境変数によって指定されたディレクトリで、ランタイムがアセンブリの検索を行うかどうかを指定します。  
  
 \<configuration>  
\<ランタイム >  
\<developmentMode >  
  
## <a name="syntax"></a>構文  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|**developerInstallation**|DEVPATH 環境変数によって指定されたディレクトリで、ランタイムがアセンブリの検索を行うかどうかを指定します。|  
  
## <a name="developerinstallation-attribute"></a>developerInstallation 属性  
  
|値|説明|  
|-----------|-----------------|  
|**true**|DEVPATH 環境変数で指定したディレクトリ内のアセンブリを検索します。|  
|**false**|DEVPATH 環境変数で指定したディレクトリ内のアセンブリを検索しません。 これは、既定値です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|アセンブリのバインディングとガベージ コレクションに関する情報が含まれています。|  
  
## <a name="remarks"></a>コメント  
 この設定を使用して、開発時のみです。 ランタイムは、DEVPATH で見つかった厳密な名前のアセンブリのバージョンをチェックしません。 最初に見つかったアセンブリは単に使用します。  
  
## <a name="example"></a>例  
 次の例では、DEVPATH 環境変数で指定したディレクトリ内のアセンブリを検索するランタイムを発生させる方法を示します。  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [方法 : DEVPATH を使用してアセンブリを指定する](../../../../../docs/framework/configure-apps/how-to-locate-assemblies-by-using-devpath.md)
