---
title: "&lt;loadFromRemoteSources&gt; 要素 | Microsoft Docs"
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
  - "loadFromRemoteSources 要素"
  - "<loadFromRemoteSources> 要素"
ms.assetid: 006d1280-2ac3-4db6-a984-a3d4e275046a
caps.latest.revision: 31
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 31
---
# &lt;loadFromRemoteSources&gt; 要素
リモート ソースからのアセンブリに完全信頼を与えるかどうかを指定します。  
  
> [!NOTE]
>  Visual Studio プロジェクトのエラー一覧に表示されたエラー メッセージ、またはビルド エラーによってこのトピックにたどり着いた場合は、「[方法: Visual Studio で Web からダウンロードしたアセンブリを使用する](http://msdn.microsoft.com/ja-jp/d8635b63-89a0-41aa-90f4-f351b2111070)」を参照してください。  
  
## 構文  
  
```  
<loadFromRemoteSources    
   enabled="true|false"/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`enabled`|必須の属性です。<br /><br /> リモート ソースから読み込まれるアセンブリに完全信頼を与えるかどうかを指定します。|  
  
## enabled 属性  
  
|値|説明|  
|-------|--------|  
|`false`|リモート ソースからのアプリケーションに完全信頼を与えません。  これは、既定の設定です。|  
|`true`|リモート ソースからのアプリケーションに完全信頼を与えます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|`configuration`|共通言語ランタイムおよび .NET Framework アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
|`runtime`|ランタイム初期化オプションに関する情報を含んでいます。|  
  
## 解説  
 .NET Framework Version 3.5 以前のバージョンでは、リモートの場所からアセンブリを読み込んだ場合、そのアセンブリは、読み込み先のゾーンに応じた許可セットが与えられた部分的に信頼されるアセンブリとして実行されていました。  たとえば、Web サイトからアセンブリを読み込んだら、インターネット ゾーンに読み込まれ、インターネット アクセス許可セットが与えられていました。  つまり、このようなアセンブリはインターネット サンドボックスで実行されていました。  [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] 以降のバージョンでそのアセンブリを実行しようとすると、例外がスローされます; \([方法 : サンドボックスで部分信頼コードを実行する](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)を参照してください\) 明示的にアセンブリのサンドボックスを作成したり、完全信頼で実行します。  
  
 `<loadFromRemoteSources>` 要素は、.NET Framework の以前のバージョンで部分的に信頼される実行するアセンブリが [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 以降で完全に信頼されて実行されるように指定することができます。  既定で、リモート アセンブリは [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 以降では実行されません。  リモート アセンブリを実行するには、完全信頼として実行するか、テストを実行するため <xref:System.AppDomain> サンドボックスを作成する必要があります。  
  
> [!NOTE]
>  [!INCLUDE[net_v45](../../../../../includes/net-v45-md.md)]では、ローカル ネットワークの共有のアセンブリを完全信頼として、既定で実行して; `<loadFromRemoteSources>` 要素を有効にする必要はありません。  
  
> [!NOTE]
>  Web からコピーされたアプリケーションは、ローカル コンピューターにある場合でも、フラグが立てられ Web アプリケーションとして Windows によって異なります。  ファイルのプロパティを変更することにより、この指定を変更できます。または、`<loadFromRemoteSources>` 要素を使用して、アセンブリに完全信頼を与えることもできます。  別の方法として、オペレーティング システムがフラグを付けたローカル アセンブリを読み込むために <xref:System.Reflection.Assembly.UnsafeLoadFrom%2A> のメソッドを使用して、Web から読み込まれますです。  
  
 この要素の `enabled` 属性は、コード アクセス セキュリティ \(CAS: Code Access Security\) が無効になっている場合にのみ有効です。  [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)] 以降のバージョンでは、CAS ポリシーは既定で無効になっています。  `enabled` を `true` に設定すると、リモート アプリケーションには完全信頼が与えられます。  
  
 `<loadFromRemoteSources>` の `enabled` が `true` に設定されていない場合は、次の状況で例外がスローされます。  
  
-   現在のドメインのサンドボックス化の動作が [!INCLUDE[net_v35_short](../../../../../includes/net-v35-short-md.md)] での動作と異なる。  この場合、CAS ポリシーを無効にし、現在のドメインがサンドボックス化されないようにする必要があります。  
  
-   読み込まれるアセンブリが `MyComputer` ゾーンからのアセンブリではない。  
  
> [!NOTE]
>  Windows Virtual PC アプリケーションの <xref:System.IO.FileLoadException> は、ホスト コンピューターのリンクされたフォルダーからファイルを読み込もうとしたときに発生することがあります。  このエラーは、リンクされたフォルダーからファイルを読み込むときに発生する可能性があります \([リモート デスクトップ サービス](http://go.microsoft.com/fwlink/?LinkId=182775) ターミナル サービス\)。  例外を回避するには、`enabled` を `true` に設定します。  
  
 `<loadFromRemoteSources>` 要素を `true` に設定すると、この例外がスローされなくなります。  この設定により、読み込まれたアセンブリを共通言語ランタイムに依存してセキュリティ目的でサンドボックス化せずに、完全信頼アセンブリとして実行できるように指定できます。  
  
> [!IMPORTANT]
>  アセンブリを完全に信頼して実行しない場合は、この構成要素を設定しないでください。  代わりに、アセンブリの読み込み先としてサンドボックス化された <xref:System.AppDomain> を作成してください。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルで使用するそのほかの構成ファイルのコンテキストで使用できます。  詳細について、.NET のセキュリティ ブログ記事を [CAS ポリシーの暗黙の使用: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839) 参照します。  
  
## 使用例  
 リモート ソースからのアプリケーションに完全信頼を与える方法を次の例に示します。  
  
```  
<configuration>  
   <runtime>  
      <loadFromRemoteSources enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## 参照  
 [CAS ポリシーの暗黙の使用: loadFromRemoteSources](http://go.microsoft.com/fwlink/p/?LinkId=266839)   
 [方法 : サンドボックスで部分信頼コードを実行する](../../../../../docs/framework/misc/how-to-run-partially-trusted-code-in-a-sandbox.md)   
 [ランタイム設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)   
 [構成ファイル スキーマ](../../../../../docs/framework/configure-apps/file-schema/index.md)