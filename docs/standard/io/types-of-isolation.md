---
title: "分離のタイプ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- storing data using isolated storage, accessing isolated storage
- storing data using isolated storage, isolation types
- authentication [.NET Framework], isolated storage
- assemblies [.NET Framework], identity
- isolated storage, accessing
- data storage using isolated storage, isolation types
- data storage using isolated storage, accessing isolated storage
- domain identity
- isolated storage, types
- user authentication, isolated storage
ms.assetid: 14812988-473f-44ae-b75f-fd5c2f21fb7b
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6b07c090a381925f5330a820214126a121d3790b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="types-of-isolation"></a>分離のタイプ
分離ストレージへのアクセスは、常に作成したユーザーを制限します。 この種の分離を実装するのには、共通言語ランタイムは、これは、コードが実行されているストアが開かれたときに、プロセスに関連付けられた id を同じオペレーティング システムが認識されると、ユーザー id の概念に使用します。 この id は、認証されたユーザー id が、権限借用を動的に変更する現在のユーザーの id が発生することができます。  
  
 分離ストレージへのアクセスは、アプリケーションのドメインとアセンブリ、またはアセンブリだけに関連付けられた id に従って制限もあります。 ランタイムは、次の方法でこれらの id を取得します。  
  
-   ドメイン id では、可能性のある web アプリケーションの場合、完全な URL と、アプリケーションの証拠を表します。 シェルでホストされているコードでは、ドメイン id がに基づいて、アプリケーションのディレクトリ パス。 C:\Office\MyApp.exe パスから、実行可能ファイルが実行される場合など、ドメイン id では、C:\Office\MyApp.exe になります。  
  
-   アセンブリ id は、アセンブリの証拠です。 アセンブリの可能性がある暗号化デジタル署名から取得できます[厳密な名前](../../../docs/framework/app-domains/strong-named-assemblies.md)のソフトウェア発行元、アセンブリ、またはその URL の id。 厳密な名前とソフトウェアの発行元の id の両方のアセンブリがある、ソフトウェアの発行元 id が使用されます。 アセンブリが、インターネットを起源が署名されていない場合は、URL の id が使用されます。 アセンブリと厳密な名前の詳細については、次を参照してください。[アセンブリを使用したプログラミング](../../../docs/framework/app-domains/programming-with-assemblies.md)です。  
  
-   ローミング ストアは、ローミング ユーザー プロファイルを持つユーザーと共に移動します。 ファイルは、ネットワーク ディレクトリに書き込まれ、ユーザーがログインする任意のコンピューターにダウンロードされます。 移動ユーザー プロファイルの詳細については、次を参照してください。<xref:System.IO.IsolatedStorage.IsolatedStorageScope.Roaming?displayProperty=nameWithType>です。  
  
 ユーザー、ドメイン、およびアセンブリ id の概念を組み合わせることにより、分離ストレージは、それぞれが独自の用途を持つ次の方法でデータを特定できます。  
  
-   [ユーザーおよびアセンブリによる分離](#UserAssembly)  
  
-   [ユーザー、ドメイン、およびアセンブリによる分離](#UserDomainAssembly)  
  
 これらの分離のいずれかは、移動ユーザー プロファイルと組み合わせることができます。 詳細については、セクションを参照して[分離ストレージとローミング](#Roaming)です。  
  
 次の図は、さまざまなスコープでのストアの分離方法を示します。  
  
 ![ユーザーおよびアセンブリによる分離](../../../docs/standard/io/media/typesofisolation.gif "typesofisolation")  
分離ストレージの種類  
  
 を除き、ストアを移動するには、分離ストレージは常に暗黙的にコンピューター別に分離は、特定のコンピューターに対してローカルな記憶域機能を使用しているために注意してください。  
  
> [!IMPORTANT]
>  分離ストレージは [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリでは使用できません。 代わりに、 `Windows.Storage` API に含まれる [!INCLUDE[wrt](../../../includes/wrt-md.md)] 名前空間内のアプリケーション データ クラスを使用して、ローカル データとローカル ファイルを格納します。 詳細については、Windows デベロッパー センターの [アプリケーション データ](http://go.microsoft.com/fwlink/?LinkId=229175) に関する説明を参照してください。  
  
<a name="UserAssembly"></a>   
## <a name="isolation-by-user-and-assembly"></a>ユーザーおよびアセンブリによる分離  
 データを使用するアセンブリを格納する任意のアプリケーションのドメインからアクセスできる必要があります、ときにユーザーおよびアセンブリによる分離が適しています。 通常、このような状況では、複数のアプリケーション全体に適用され、ユーザーの名前やライセンス情報など、特定のアプリケーションに関連付けられていないデータを格納する分離ストレージが使用されます。 ユーザーおよびアセンブリ別に分離された記憶域にアクセスするにコードをアプリケーション間で情報を転送するために信頼する必要があります。 通常、ユーザーおよびアセンブリによる分離では、イントラネットではなく、インターネットが許可されます。 静的なを呼び出して<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A?displayProperty=nameWithType>メソッドおよびユーザーとアセンブリに渡すこと<xref:System.IO.IsolatedStorage.IsolatedStorageScope>このような分離ストレージを返します。  
  
 次のコード例では、ユーザーおよびアセンブリ別に分離されたストアを取得します。 ストアを介してアクセスできる、`isoFile`オブジェクト。  
  
 [!code-cpp[Conceptual.IsolatedStorage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#17)]
 [!code-csharp[Conceptual.IsolatedStorage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#17)]
 [!code-vb[Conceptual.IsolatedStorage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#17)]  
  
 証拠パラメーターを使用する例は、次を参照してください。<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%28System.IO.IsolatedStorage.IsolatedStorageScope%2CSystem.Security.Policy.Evidence%2CSystem.Type%2CSystem.Security.Policy.Evidence%2CSystem.Type%29>です。  
  
 <xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetUserStoreForAssembly%2A>メソッドは、次のコード例に示すように、簡単な方法として使用します。 ローミングに対応するストアを開くには、このショートカットを使用できません。使用して<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>このような場合です。  
  
 [!code-cpp[Conceptual.IsolatedStorage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source11.cpp#18)]
 [!code-csharp[Conceptual.IsolatedStorage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source11.cs#18)]
 [!code-vb[Conceptual.IsolatedStorage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source11.vb#18)]  
  
<a name="UserDomainAssembly"></a>   
## <a name="isolation-by-user-domain-and-assembly"></a>ユーザー、ドメイン、およびアセンブリによる分離  
 アプリケーションでは、プライベート データ ストアを必要とするサード パーティ製のアセンブリを使用する場合は、プライベート データを格納する分離ストレージを使用できます。 ユーザー、ドメイン、およびアセンブリによる分離確実にだけで、特定のアセンブリ内のコードは、データにアクセスできるアセンブリが、アセンブリには、ストアが作成されるときに実行されていたアプリケーションで使用される場合にのみと、ストアの作成対象のユーザーが実行時にのみ、 アプリケーション。 ユーザー、ドメイン、およびアセンブリによる分離では、他のアプリケーションへのデータの漏洩からサードパーティ製のアセンブリが保持されます。 この分離型は、分離ストレージを使用するが、不明などの種類の分離を使用することがわかっている場合、既定の選択肢をする必要があります。 呼び出す、静的な<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>メソッドの<xref:System.IO.IsolatedStorage.IsolatedStorageFile>を渡すユーザー、ドメイン、およびアセンブリと<xref:System.IO.IsolatedStorage.IsolatedStorageScope>このような分離ストレージを返します。  
  
 次のコード例では、ユーザー、ドメイン、およびアセンブリ別に分離されたストアを取得します。 ストアを介してアクセスできる、`isoFile`オブジェクト。  
  
 [!code-cpp[Conceptual.IsolatedStorage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#14)]
 [!code-csharp[Conceptual.IsolatedStorage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#14)]
 [!code-vb[Conceptual.IsolatedStorage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#14)]  
  
 別の方法を次のコード例に示すように簡単な方法として使用します。 ローミングに対応するストアを開くには、このショートカットを使用できません。使用して<xref:System.IO.IsolatedStorage.IsolatedStorageFile.GetStore%2A>このような場合です。  
  
 [!code-cpp[Conceptual.IsolatedStorage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source10.cpp#15)]
 [!code-csharp[Conceptual.IsolatedStorage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source10.cs#15)]
 [!code-vb[Conceptual.IsolatedStorage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source10.vb#15)]  
  
<a name="Roaming"></a>   
## <a name="isolated-storage-and-roaming"></a>分離ストレージとローミング  
 移動ユーザー プロファイルは、ユーザーがネットワーク上の id を設定し、その id を使用して、個人用に設定されたすべての設定に実行するすべてのネットワーク コンピューターにログインできるようにする Windows の機能です。 分離ストレージを使用したアセンブリでは、ユーザーの分離ストレージは、ローミング ユーザー プロファイルと移動する必要がありますを指定できます。 ユーザー、ドメイン、およびアセンブリ別、と共に、ユーザーおよびアセンブリによる分離または分離を使用したしてローミングを使用することがことができます。 ローミングのスコープを使用しない場合、ローミング ユーザー プロファイルを使用する場合でもストアは移動しません。  
  
 次のコード例では、ユーザーおよびアセンブリ別に分離されたローミング ストアを取得します。 ストアを介してアクセスできる、`isoFile`オブジェクト。  
  
 [!code-cpp[Conceptual.IsolatedStorage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#11)]
 [!code-csharp[Conceptual.IsolatedStorage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#11)]
 [!code-vb[Conceptual.IsolatedStorage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#11)]  
  
 ユーザー、ドメイン、およびアプリケーション別に分離されたローミング ストアを作成するのには、ドメイン スコープを追加できます。 次のコード例を示します。  
  
 [!code-cpp[Conceptual.IsolatedStorage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.isolatedstorage/cpp/source9.cpp#12)]
 [!code-csharp[Conceptual.IsolatedStorage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.isolatedstorage/cs/source9.cs#12)]
 [!code-vb[Conceptual.IsolatedStorage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.isolatedstorage/vb/source9.vb#12)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.IO.IsolatedStorage.IsolatedStorageScope>  
 [分離ストレージ](../../../docs/standard/io/isolated-storage.md)
