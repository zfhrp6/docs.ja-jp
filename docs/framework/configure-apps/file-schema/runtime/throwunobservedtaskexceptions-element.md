---
title: "&lt;ThrowUnobservedTaskExceptions&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<ThrowUnobservedTaskExceptions> 要素"
  - "ThrowUnobservedTaskExceptions 要素"
ms.assetid: cea7e588-8b8d-48d2-9ad5-8feaf3642c18
caps.latest.revision: 6
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 6
---
# &lt;ThrowUnobservedTaskExceptions&gt; 要素
未処理の例外を実行中のプロセスを停止する必要があるかどうかを指定します。  
  
## 構文  
  
```vb  
<ThrowUnobservedTaskExceptions  
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> 未処理の例外を実行中のプロセスを停止する必要があるかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|未処理の例外の実行中のプロセスを終了することはありません。  これは、既定の設定です。|  
|`true`|未処理の例外の実行中のプロセスを終了します。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
|||  
  
## 解説  
 <xref:System.Threading.Tasks.Task> に関連付けられている例外が確認されていない場合、<xref:System.Threading.Tasks.Task.Wait%2A> 操作がない、親が接続されておらず、<xref:System.Threading.Tasks.Task.Exception%2A?displayProperty=fullName> のタスクの Exception プロパティは無視して見なされますに読み込まれません。  
  
 [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)]で、<xref:System.Threading.Tasks.Task> が無視された例外があるガベージ コレクションに既定で、ファイナライザーが例外をスローし、プロセスが終了します。  プロセスの終了がガベージ コレクションと終了のタイミングによって決まります。  
  
 開発者がタスクに基づく非同期コードを記述できる [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)] が変更された無視された例外に対してこの既定の動作を、を簡単にするには、  無視された例外は、<xref:System.Threading.Tasks.TaskScheduler.UnobservedTaskException> イベントを発生させますが既定で、プロセスは終了しません。  代わりに、例外がイベント ハンドラーが例外を確認するかどうかをイベントが発生させた後に関係なく、無視されます。  
  
 [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]のアプリケーション構成ファイルで例外をスローする可能性の [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] の動作を有効にするために [\<ThrowUnobservedTaskExceptions\> 要素](../../../../../docs/framework/configure-apps/file-schema/runtime/throwunobservedtaskexceptions-element.md) を使用できます。  
  
 また、次の 1 種類の例外の動作を指定する:  
  
-   環境変数 `COMPlus_ThrowUnobservedTaskExceptions` \(`set COMPlus_ThrowUnobservedTaskExceptions=1`\) に設定します。  
  
-   レジストリ ThrowUnobservedTaskExceptions DWORD 値を設定して \= HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework キーの 1。  
  
## 使用例  
 次の例では、アプリケーション構成ファイルを使用してタスクの例外をスローするようにする方法を示します。  
  
```  
<configuration>   
    <runtime>   
        <ThrowUnobservedTaskExceptions enabled="true"/>   
    </runtime>   
</configuration>  
  
```  
  
## 使用例  
 無視された例外がタスクからスローされるかを次の例に示します。  コードは、解放されたプログラムとして正しく動作するために実行する必要があります。  
  
 [!code-csharp[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/csharp/VS_Snippets_CLR/throwunobservedtaskexceptions/cs/program.cs#1)]
 [!code-vb[ThrowUnobservedTaskExceptions#1](../../../../../samples/snippets/visualbasic/VS_Snippets_CLR/throwunobservedtaskexceptions/vb/program.vb#1)]  
  
## 参照  
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)