---
title: "分離のタイプ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "格納 (分離ストレージを使用したデータの)、アクセス (分離ストレージへの)"
  - "格納 (分離ストレージを使用したデータの)、分離タイプ"
  - "認証 [.NET Framework]、分離ストレージ"
  - "アセンブリ [.NET Framework]、ID"
  - "分離ストレージ、アクセス"
  - "データ ストレージ (分離ストレージを使用した)、分離タイプ"
  - "データ ストレージ (分離ストレージを使用した)、アクセス (分離ストレージへの)"
  - "ドメイン ID"
  - "分離ストレージ、タイプ"
  - "ユーザー認証、分離ストレージ"
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
caps.latest.revision: 16
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 16
---
# 分離のタイプ
分離ストレージへのアクセスは、常にその分離ストレージを作成したユーザーに制限されます。  この種の分離を実装するために、共通言語ランタイムは、オペレーティング システムによって認識されるユーザー ID と同じユーザー ID、つまり、ストアを開いたときにコードを実行しているプロセスに関連付けられている ID を使用します。  この ID は認証されたユーザー ID ですが、現在のユーザーの ID は偽装によって動的に変更される場合もあります。  
  
 分離ストレージへのアクセスは、アプリケーションのドメイン、アセンブリ、またはアセンブリだけに関連付けられた ID に基づいて制限されます。  ランタイムは、これらの ID を次の方法で取得します。  
  
-   ドメイン ID は Web アプリケーションの場合は、完全な URL である可能性があるアプリケーションの証拠を表します。  シェルによってホストされるコードの場合は、ドメイン ID は、アプリケーションのディレクトリ パスが基になります。  たとえば、実行可能ファイルをパス C:\\Office\\MyApp.exe から実行する場合、ドメイン ID は C:\\Office\\MyApp.exe です。  
  
-   アセンブリ ID は、アセンブリの証拠です。  アセンブリ ID は、アセンブリの暗号化デジタル署名から取得できます。アセンブリ ID は、[厳密な名前](../../../docs/framework/app-domains/strong-named-assemblies.md)、アセンブリのソフトウェア発行元、またはアセンブリの URL ID のいずれかです。  アセンブリが厳密な名前とソフトウェア発行元 ID の両方を持つ場合は、ソフトウェア発行元 ID が使用されます。  インターネットからダウンロードされ、署名されていないアセンブリの場合は、URL ID が使用されます。  アセンブリと厳密な名前の詳細については、「[アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)」を参照してください。  
  
-   ローミング ストアは、ローミング ユーザー プロファイルを持つユーザーと共に移動します。  ファイルはネットワーク ディレクトリに書き込まれ、ユーザーがログインする任意のコンピューターにダウンロードにされます。  ローミング ユーザー プロファイルの詳細については、「<xref:System.IO.IsolatedStorage.IsolatedStorageScope?displayProperty=fullName>」を参照してください。  
  
 ユーザー ID、ドメイン ID、およびアセンブリ ID の概念を組み合わせることにより、分離ストレージは、次の 2 とおりの方法でデータを分離できます。それぞれの分離方法には、そのアクセス権限について使用法の例があります。  
  
-   [ユーザーとアセンブリ別の分離](#UserAssembly)  
  
-   [ユーザー、ドメイン、およびアセンブリ別の分離](#UserDomainAssembly)  
  
 どちらかの分離にも、ローミング ユーザー プロファイルを組み合わせることができます。  詳細については、セクション [分離ストレージとローミング](#Roaming)を参照します。  
  
 ストアを分離する方法をさまざまなスコープで示す図を次に示します。  
  
 ![ユーザーとアセンブリ別の分離](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
分離ストレージのタイプ  
  
 特定のコンピューターに固有のストレージ機能を使用するためにコンピューター別に分離されたローミング ストアを除き、分離ストレージは暗黙的常になっていることに注意してください。  
  
> [!IMPORTANT]
>  分離ストレージは [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでは使用できません。  代わりに、[!INCLUDE[wrt](../../../includes/wrt-md.md)] API に含まれる `Windows.Storage` 名前空間内のアプリケーション データ クラスを使用して、ローカル データとローカル ファイルを格納します。  詳細については、Windows デベロッパー センターの[アプリケーション データ](http://go.microsoft.com/fwlink/?LinkId=229175)に関する説明を参照してください。  
  
<a name="UserAssembly"></a>   
## ユーザーおよびアセンブリによる分離  
 データ ストアを使用するアセンブリは、アプリケーションのドメインからアクセスできるようにする必要がある場合は、ユーザーおよびアセンブリ別の分離が適しています。  一般に、このような場面では、分離ストレージは複数のアプリケーションにまたがって適用されるデータを格納するために使用され、ユーザーの名前やライセンス情報などの特定のアプリケーションには関連付けられません。  ユーザーおよびアセンブリ別に分離されたストレージにアクセスするには、アプリケーション間で情報を転送する権限を持っている必要があります。  一般に、ユーザーおよびアセンブリ別の分離は、イントラネットでは可能ですが、インターネットでは使用できません。  静的な <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=fullName> のメソッドを呼び出し、この種類の分離のユーザーおよびアセンブリ <xref:System.IO.IsolatedStorage.IsolatedStorageScope> からのストレージに渡します。  
  
 次のコード例は、ユーザーおよびアセンブリ別に分離されたストアを取得します。  ストアには、`isoFile`  オブジェクトを通じてアクセスできます。  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 証拠パラメーターの使用例については、<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>を参照してください。  
  
 簡便な方法として <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A> メソッドを使用するコード例を次に示します。  この方法は、ローミング可能なストアを開くときは使用できません。; <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> のような場合に使用します。  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## ユーザー、ドメイン、およびアセンブリによる分離  
 アプリケーションのプライベートなデータ ストアを必要とするサードパーティのアセンブリを使用する場合は、プライベート データを格納する目的で分離ストレージを使用できます。  ユーザー、ドメイン、およびアセンブリ別の分離では、データにアクセスできるのは、所定のアセンブリのコードだけであり、またそのストアの作成時に実行中であったアプリケーションがそのストアを使用し、さらにそのストアを所有するユーザーがそのアプリケーションを実行しているときだけです。  ユーザー、ドメイン、およびアセンブリ別の分離では、サードパーティのアセンブリがほかのアプリケーションにデータをリークするのを防ぐことができます。  分離ストレージを使用する必要があり、どのタイプの分離を使用するか判断できない場合は、このタイプの分離を既定として選択してください。  <xref:System.IO.IsolatedStorage.IsolatedStorageFile> の <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> の静的なメソッドを呼び出し、ユーザー、ドメイン、およびアセンブリ <xref:System.IO.IsolatedStorage.IsolatedStorageScope> ではこの種類の分離ストレージが返されます。  
  
 ユーザー、ドメイン、およびアセンブリ別に分離されたストアを取得するコード例を次に示します。  ストアには、`isoFile` オブジェクトを通じてアクセスできます。  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 簡便な方法として、別のメソッドを使用するコード例を次に示します。  この方法は、ローミング可能なストアを開くときは使用できません。; <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A> のような場合に使用します。  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## 分離ストレージとローミング  
 ローミング ユーザー プロファイルはユーザーがネットワークの ID を設定し、ネットワーク コンピューターにログインするときにその ID が使用できるすべてのパーソナル化された設定に対する Windows 機能です。  分離ストレージを使用するアセンブリは、ユーザーの分離ストレージとローミング ユーザー プロファイルとともに移動するように指定できます。  ローミングは、ユーザーやアセンブリ別の分離、またはユーザー、ドメイン、およびアセンブリ別の分離と組み合わせて使用できます。  ローミング スコープが使用されていない場合は、ローミング ユーザー プロファイルを使用しても、ストアは移動しません。  
  
 ユーザーおよびアセンブリ別に分離されたローミング ストアを取得するコード例を次に示します。  ストアには、`isoFile`  オブジェクトを通じてアクセスできます。  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 ドメイン スコープを追加すると、ユーザー、ドメイン、およびアプリケーション別に分離されたローミング ストアを作成できます。  ドメイン スコープを追加するコード例を次に示します。  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## 参照  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>   
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)