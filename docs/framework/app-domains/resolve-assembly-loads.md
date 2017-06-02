---
title: "アセンブリ読み込みの解決 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-bcl"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アセンブリ [.NET Framework]、解決 (読み込みを)"
  - "アプリケーション ドメイン、読み込み (アセンブリを)"
  - "解決 (アセンブリ読み込みを)"
  - "アセンブリ [.NET Framework]、読み込み"
  - "アプリケーション ドメイン、解決 (アセンブリ読み込みを)"
ms.assetid: 5099e549-f4fd-49fb-a290-549edd456c6a
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# アセンブリ読み込みの解決
.NET Framework には、アセンブリの読み込みをより細かく制御する必要があるアプリケーション向けに <xref:System.AppDomain.AssemblyResolve?displayProperty=fullName> イベントが用意されています。  このイベントを処理することにより、アプリケーションでは、アセンブリを通常のプローブ パス以外から読み込みコンテキストに読み込んだり、読み込むアセンブリのバージョンを複数選択したり、動的アセンブリを生成して返したりすることができます。  このトピックでは、<xref:System.AppDomain.AssemblyResolve> イベントの処理に関するガイダンスを示します。  
  
> [!NOTE]
>  リフレクション専用コンテキストでアセンブリの読み込みを解決する場合は、代わりに <xref:System.AppDomain.ReflectionOnlyAssemblyResolve?displayProperty=fullName> イベントを使用します。  
  
## AssemblyResolve イベントの動作  
 <xref:System.AppDomain.AssemblyResolve> イベントのハンドラーを登録すると、ランタイムで名前によるアセンブリへのバインドに失敗した場合に、必ずこのハンドラーが呼び出されます。  たとえば、ユーザー コードから次のメソッドを呼び出すと、<xref:System.AppDomain.AssemblyResolve> イベントが発生することがあります。  
  
-   読み込むアセンブリの表示名を表す文字列 \(<xref:System.Reflection.Assembly.FullName%2A?displayProperty=fullName> プロパティによって返される文字列\) を最初の引数として指定する <xref:System.AppDomain.Load%2A?displayProperty=fullName> メソッド オーバーロードまたは <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> メソッド オーバーロード。  
  
-   読み込むアセンブリを識別する <xref:System.Reflection.AssemblyName> オブジェクトを最初の引数として指定する <xref:System.AppDomain.Load%2A?displayProperty=fullName> メソッド オーバーロードまたは <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> メソッド オーバーロード。  
  
-   <xref:System.Reflection.Assembly.LoadWithPartialName%2A?displayProperty=fullName> メソッド オーバーロード。  
  
-   別のアプリケーション ドメインのオブジェクトをインスタンス化する <xref:System.AppDomain.CreateInstance%2A?displayProperty=fullName> または <xref:System.AppDomain.CreateInstanceAndUnwrap%2A?displayProperty=fullName> メソッド オーバーロード。  
  
### イベント ハンドラーで実行する処理  
 <xref:System.AppDomain.AssemblyResolve> イベントのハンドラーは、読み込むアセンブリの表示名を <xref:System.ResolveEventArgs.Name%2A?displayProperty=fullName> プロパティで受け取ります。  アセンブリ名を認識できない場合、ハンドラーは null \(Visual Basic の場合は `Nothing`、Visual C\+\+ の場合は `nullptr`\) を返します。  
  
 アセンブリ名を認識すると、ハンドラーは要求を満たすアセンブリを読み込んで返すことができます。  サンプルのシナリオをいくつか示します。  
  
-   アセンブリのバージョンの場所がわかっている場合、<xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> メソッドまたは <xref:System.Reflection.Assembly.LoadFile%2A?displayProperty=fullName> メソッドを使用してアセンブリを読み込み、正常に読み込まれた場合はそのアセンブリを返すことができます。  
  
-   アセンブリがバイト配列として格納されているデータベースにアクセスできる場合、バイト配列を受け取るいずれかの <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> メソッド オーバーロードを使用してバイト配列を読み込むことができます。  
  
-   動的アセンブリを生成して返すことができます。  
  
> [!NOTE]
>  このハンドラーでアセンブリを読み込むときは、読み込み元コンテキストまたは読み込みコンテキストに読み込むか、コンテキストなしで読み込む必要があります。  <xref:System.Reflection.Assembly.ReflectionOnlyLoad%2A?displayProperty=fullName> または <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=fullName> メソッドを使用してリフレクション専用コンテキストにアセンブリを読み込もうとすると、<xref:System.AppDomain.AssemblyResolve> イベントを発生させた読み込みは失敗します。  
  
 イベント ハンドラーは、適切なアセンブリを返す必要があります。  ハンドラーでは、<xref:System.ResolveEventArgs.Name%2A?displayProperty=fullName> プロパティの値を <xref:System.Reflection.AssemblyName.%23ctor%28System.String%29> コンストラクターに渡すことによって、要求されたアセンブリの表示名を解析できます。  [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、<xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName> プロパティを使用して、現在の要求が別のアセンブリと依存関係にあるかどうかを確認できます。  この情報は、依存関係を満たすアセンブリを識別するうえで役立ちます。  
  
 イベント ハンドラーは、要求されたバージョンとは異なるバージョンのアセンブリを返すことがあります。  
  
 ほとんどの場合、ハンドラーによって返されるアセンブリは、ハンドラーが読み込んだコンテキストに関係なく、読み込みコンテキストで返されます。  たとえば、ハンドラーが <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=fullName> メソッドを使用して読み込み元コンテキストにアセンブリを読み込んだ場合、ハンドラーからアセンブリが返されるときは読み込みコンテキストで返されます。  ただし、次の場合は、アセンブリがハンドラーからコンテキストなしで返されます。  
  
-   ハンドラーがコンテキストなしでアセンブリを読み込んだ場合。  
  
-   <xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName> プロパティが null でない場合。  
  
-   要求元のアセンブリ \(<xref:System.ResolveEventArgs.RequestingAssembly%2A?displayProperty=fullName> プロパティによって返されるアセンブリ\) がコンテキストなしで読み込まれている場合。  
  
 コンテキストの詳細については、<xref:System.Reflection.Assembly.LoadFrom%28System.String%29?displayProperty=fullName> メソッド オーバーロードのトピックを参照してください。  
  
 同じアセンブリの複数のバージョンを同じアプリケーション ドメインに読み込むこともできますが、  型の割り当てで問題が生じる可能性があるため、この方法はお勧めしません。  「[アセンブリの読み込みのベスト プラクティス](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)」を参照してください。  
  
### イベント ハンドラーで実行すべきでない処理  
 <xref:System.AppDomain.AssemblyResolve> イベントを処理する際の基本的なルールとして、認識できないアセンブリは返さないようにしてください。  ハンドラーを記述するときは、このイベントが発生する原因となる可能性があるアセンブリを把握しておく必要があります。  それ以外のアセンブリについては、null を返すようにしてください。  
  
> [!IMPORTANT]
>  [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] 以降では、<xref:System.AppDomain.AssemblyResolve> イベントはサテライト アセンブリに対して発生します。  この変更は、以前のバージョンの .NET Framework 用に記述されたイベント ハンドラーで、すべてのアセンブリ読み込み要求を解決しようとする場合に影響します。  認識できないアセンブリを無視するイベント ハンドラーには、この変更による影響はありません。それらのイベント ハンドラーは null を返し、通常のフォールバック機構に従います。  
  
 イベント ハンドラーでアセンブリを読み込むときに、<xref:System.AppDomain.AssemblyResolve> イベントを再帰的に発生させる可能性がある <xref:System.AppDomain.Load%2A?displayProperty=fullName> メソッド オーバーロードまたは <xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName> メソッド オーバーロードは使用しないでください。これを使用すると、スタック オーバーフローが発生する可能性があります \(前述の一覧を参照してください\)。これは、読み込み要求の例外処理を指定した場合でも発生します。すべてのイベント ハンドラーから制御が戻るまでは例外がスローされないからです。  したがって、次のコードでは、`MyAssembly` が見つからないとスタック オーバーフローが発生します。  
  
 [!code-cpp[AssemblyResolveRecursive#1](../../../samples/snippets/cpp/VS_Snippets_CLR/assemblyresolverecursive/cpp/example.cpp#1)]
 [!code-csharp[AssemblyResolveRecursive#1](../../../samples/snippets/csharp/VS_Snippets_CLR/assemblyresolverecursive/cs/example.cs#1)]
 [!code-vb[AssemblyResolveRecursive#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/assemblyresolverecursive/vb/example.vb#1)]  
  
## 参照  
 [アセンブリの読み込みのベスト プラクティス](../../../docs/framework/deployment/best-practices-for-assembly-loading.md)   
 [アプリケーション ドメインの使用](../../../docs/framework/app-domains/use.md)