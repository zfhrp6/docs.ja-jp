---
title: '&lt;ThrowUnobservedTaskExceptions&gt;要素'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ThrowUnobservedTaskExceptions element
- <ThrowUnobservedTaskExceptions> element
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3f72bedbaaf0b15ade7ff6b7b8c3edcdfd3fda6d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749427"
---
# <a name="ltthrowunobservedtaskexceptionsgt-element"></a>&lt;ThrowUnobservedTaskExceptions&gt;要素
タスクがハンドルされない例外によって実行中のプロセスを終了するかどうかを指定します。  
  
 \<configuration>  
\<ランタイム >  
\<ThrowUnobservedTaskExceptions >  
  
## <a name="syntax"></a>構文  
  
```xml  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`enabled`|必須の属性です。<br /><br /> タスクがハンドルされない例外が実行中のプロセスを終了するかどうかを指定します。|  
  
## <a name="enabled-attribute"></a>enabled 属性  
  
|値|説明|  
|-----------|-----------------|  
|`false`|タスクがハンドルされない例外に対して実行中のプロセスを終了しません。 既定値です。|  
|`true`|タスクがハンドルされない例外に対して実行中のプロセスを終了します。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
|||  
  
## <a name="remarks"></a>コメント  
 例外に関連付けられている場合、<xref:System.Threading.Tasks.Task>が監視されていません、あるありません<xref:System.Threading.Tasks.Task.Wait%2A>操作、親はアタッチされていない、および<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=nameWithType>プロパティを読み取れませんでした、タスクの例外は監視できないと見なされます。  
  
 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]により、場合は、既定、<xref:System.Threading.Tasks.Task>を持つ、観察されない例外はガベージ コレクション、ファイナライザーが例外をスローし、プロセスを終了します。 プロセスの終了は、ガベージ コレクションと終了処理のタイミングによって決まります。  
  
 タスクに基づく非同期コードを記述する開発者向け容易にできるように、[!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]観察されない例外のこの既定の動作を変更します。 無視された例外が、<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException>イベントが発生する、既定では、プロセスを終了しません。 代わりに、イベント ハンドラーが例外を監視するかどうかに関係なく、イベントが発生した後に、例外が無視されます。  
  
 [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]、使用することができます、 [ \<ThrowUnobservedTaskExceptions > 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md)を有効にする、アプリケーション構成ファイルで、[!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)]の例外をスローして動作します。  
  
 次の方法のいずれかで例外の動作を指定することもできます。  
  
-   環境変数を設定して`COMPlus_ThrowUnobservedTaskExceptions`(`set COMPlus_ThrowUnobservedTaskExceptions=1`)。  
  
-   レジストリ DWORD を設定して値 ThrowUnobservedTaskExceptions = 1、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft に\\です。NETFramework キー。  
  
## <a name="example"></a>例  
 次の例では、アプリケーション構成ファイルを使用して、タスクでの例外のスローを有効にする方法を示します。  
  
```xml  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
```  
  
## <a name="example"></a>例  
 次の例では、タスクから観察されない例外をスローする方法を示します。 リリースされたプログラムを正しく動作としては、コードを実行する必要があります。  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## <a name="see-also"></a>関連項目  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)
