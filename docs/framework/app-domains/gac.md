---
title: "グローバル アセンブリ キャッシュ (GAC) | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- GAC (global assembly cache)
- ACLs [.NET Framework]
- global assembly cache
- cache [.NET Framework], global assembly cache
- global assembly cache, about
- access control lists [.NET Framework]
ms.assetid: cf5eacd0-d3ec-4879-b6da-5fd5e4372202
caps.latest.revision: 13
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 0a40c6dcc51728bb069381b8af4652ce533bb08c
ms.contentlocale: ja-jp
ms.lasthandoff: 06/02/2017

---
# <a name="global-assembly-cache"></a>グローバル アセンブリ キャッシュ
共通言語ランタイムがインストールされている各コンピューターには、グローバル アセンブリ キャッシュと呼ばれる、コンピューター全体にわたって使用されるコード キャッシュがあります。 グローバル アセンブリ キャッシュは、そのコンピューター上の複数のアプリケーションで共有するように指定されたアセンブリを格納します。  
  
 アセンブリを共有するには、必要な場合にだけそれらのアセンブリをグローバル アセンブリ キャッシュにインストールします。 一般的には、明らかにアセンブリを共有する必要がある場合を除いて、アセンブリの依存関係はプライベートにし、アセンブリはアプリケーション ディレクトリに配置します。 また、COM 相互運用またはアンマネージ コードからアセンブリにアクセスできるようにするために、アセンブリをグローバル アセンブリ キャッシュにインストールする必要はありません。  
  
> [!NOTE]
>  アセンブリをグローバル アセンブリ キャッシュにインストールしないようにする必要がある場合もあります。 アプリケーションを構成するアセンブリの 1 つをグローバル アセンブリ キャッシュに配置した場合は、アプリケーション ディレクトリをコピーする **xcopy** コマンドを使用してアプリケーションをレプリケートしたりインストールしたりすることはできなくなります。 この場合、グローバル アセンブリ キャッシュ内に配置したアセンブリも移動する必要があります。  
  
 アセンブリをグローバル アセンブリ キャッシュに配置するには、次の 2 つの方法があります。  
  
-   グローバル アセンブリ キャッシュを扱うことができるようにデザインされたインストーラーを使用する。 これは、アセンブリをグローバル アセンブリ キャッシュにインストールするために一般的に使用される方法です。  
  
-   [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]に用意されている[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) という開発者ツールを使用する。  
  
    > [!NOTE]
    >  配置時にアセンブリをグローバル アセンブリ キャッシュにインストールするには、Windows Installer を使用する必要があります。 グローバル アセンブリ キャッシュ ツールの使用は、開発時のみに限定してください。グローバル アセンブリ キャッシュ ツールでは、Windows インストーラーを使用した場合に提供されるアセンブリ参照カウントやその他の機能が提供されません。  
  
 .NET Framework 4 以降では、グローバル アセンブリ キャッシュの既定の場所は **%windir%\Microsoft.NET\assembly** です。 .NET Framework の以前のバージョンでは、既定の場所は **%windir%\assembly** です。  
  
 通常、管理者は、書き込みおよび実行アクセスを制御するアクセス制御リスト (ACL: Access Control List) を使用して systemroot ディレクトリを保護します。 グローバル アセンブリ キャッシュは、systemroot ディレクトリのサブディレクトリにインストールされるため、このディレクトリの ACL を継承します。 グローバル アセンブリ キャッシュからファイルを削除する場合は、管理者権限を持つユーザーに対してだけ許可することをお勧めします。  
  
 グローバル アセンブリ キャッシュに配置するアセンブリには、厳密な名前を付けておく必要があります。 アセンブリをグローバル アセンブリ キャッシュに追加すると、アセンブリを構成するすべてのファイルに対して、整合性チェックが実行されます。 キャッシュはこのような整合性チェックを実行することで、ファイルが変更されたにもかかわらず、マニフェストにその変更が反映されていないなど、アセンブリに不整合が生じていないかどうかを確認します。  
  
## <a name="see-also"></a>関連項目  
 [共通言語ランタイムのアセンブリ](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md)   
 [アセンブリとグローバル アセンブリ キャッシュの使用](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)   
 [厳密な名前付きアセンブリ](../../../docs/framework/app-domains/strong-named-assemblies.md)
