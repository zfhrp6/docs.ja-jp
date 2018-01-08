---
title: "方法 : グローバル アセンブリ キャッシュにアセンブリをインストールする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- Gacutil.exe
- strong-named assemblies, global assembly cache
- global assembly cache, installing assemblies
- Global Assembly Cache tool
ms.assetid: a7e6f091-d02c-49ba-b736-7295cb0eb743
caps.latest.revision: "24"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 47867a82432ec6abe2245a0421d800c242d92b2c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-install-an-assembly-into-the-global-assembly-cache"></a>方法 : グローバル アセンブリ キャッシュにアセンブリをインストールする
厳密な名前付きのアセンブリをグローバル アセンブリ キャッシュ (GAC) にインストールには、次の 2 つの方法があります。  
  
> [!IMPORTANT]
>  GAC にインストールできるのは、厳密な名前付きのアセンブリだけです。 厳密な名前付きのアセンブリを作成する方法については、「[方法: 厳密な名前でアセンブリに署名する](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)」を参照してください。  
  
-   [Windows インストーラー](http://msdn.microsoft.com/library/windows/desktop/cc185688.aspx)を使用する。  
  
     この操作を行うには、Visual Studio 2012 および Visual Studio 2013 で、InstallShield Limited Edition プロジェクトを作成します。  
  
     これは、アセンブリをグローバル アセンブリ キャッシュに追加する最も一般的な方法です。この方法をお勧めします。 このインストーラーを使用すると、グローバル アセンブリ キャッシュ内のアセンブリの参照カウントが示されるなどの利点があります。  
  
-   [グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md) を使用する。  
  
     Gacutil.exe を使用すると、厳密な名前付きアセンブリをグローバル アセンブリ キャッシュに追加したり、グローバル アセンブリ キャッシュの内容を表示したりできます。  
  
    > [!NOTE]
    >  Gacutil.exe は開発専用です。製品アセンブリをグローバル アセンブリ キャッシュにインストールするためには使用しないでください。  
  
> [!NOTE]
>  以前のバージョンの .NET Framework では、Windows のシェル拡張機能である Shfusion.dll により、エクスプローラーでアセンブリをドラッグしてインストールすることができました。 [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] 以降では、Shfusion.dll は廃止されましたが、互換性のために残されています。  
  
### <a name="to-use-the-global-assembly-cache-tool-gacutilexe"></a>グローバル アセンブリ キャッシュ ツール (Gacutil.exe) を使用するには  
  
1.  コマンド プロンプトに次のコマンドを入力します。  
  
     **gacutil -i** \<*assembly name*>  
  
     このコマンドで、*assembly name* はグローバル アセンブリ キャッシュにインストールされるアセンブリの名前です。  
  
 ファイル名 `hello.dll` のアセンブリをグローバル アセンブリ キャッシュにインストールする例を次に示します。  
  
```  
gacutil -i hello.dll  
```  
  
 詳細については、「[グローバル アセンブリ キャッシュ ツール (Gacutil.exe)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)」を参照してください。  
  
### <a name="to-use-an-installshield-limited-edition-project"></a>InstallShield Limited Edition プロジェクトを使用するには  
  
1.  ソリューションのショートカット メニューを開き、**[追加]**、**[新しいプロジェクト]** の順に選択して、ソリューションにセットアップと配置パッケージを追加します。  
  
2.  **[新しいプロジェクトの追加]** ダイアログ ボックスの **[インストール済み]** フォルダーで、**[その他のプロジェクトの種類]**、**[セットアップと配置]**、**[InstallShield Limited Edition]** の順に選択し、プロジェクトに名前を付けます。 (プロンプトが表示されたら、InstallShield をダウンロードし、インストールしてアクティブにします。)  
  
3.  **ソリューション エクスプローラー**のプロジェクト アシスタントを使用するか、**ソリューション エクスプローラー**の番号付き手順のサブ手順を選択して、セットアップと配置プロジェクトの一般的な構成を行います。アセンブリを GAC に追加しない場合と同様にセットアップを構成します。  
  
4.  アセンブリを GAC に追加するプロセスを開始するには、**ソリューション エクスプローラー**の **[アプリケーション データの指定]** 手順の下にある **[ファイル]** を選択します。  
  
5.  **[インストール先コンピューターのフォルダー]** ペインで、**[インストール先コンピューター]** のショートカット メニューを開き、**[定義済みフォルダーの表示]**、**[GlobalAssemblyCache]** の順に選択します。  
  
6.  グローバル アセンブリ キャッシュにインストールするアセンブリを含む、ソリューション内の各プロジェクトで、次の操作を行います。  
  
    1.  **[インストール元コンピューターのフォルダー]** ペインでプロジェクトを選択します。  
  
    2.  **[インストール先コンピューターのフォルダー]** ペインで **[GlobalAssemblyCache]** を選択します。  
  
    3.  **[インストール元コンピューターのファイル]** ペインで、**[*<project_name>* のプライマリ出力]** を選択します。  
  
    4.  手順 c のファイルを **[インストール先コンピューターのファイル]** ペインにドラッグします (または、ファイルのショートカット メニューの **[コピー]** と **[貼り付け]** コマンドを使用します)。  
  
## <a name="see-also"></a>参照  
 [アセンブリとグローバル アセンブリ キャッシュの使用](../../../docs/framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [方法: グローバル アセンブリ キャッシュからアセンブリを削除する](../../../docs/framework/app-domains/how-to-remove-an-assembly-from-the-gac.md)  
 [Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](../../../docs/framework/tools/gacutil-exe-gac-tool.md)  
 [方法: 厳密な名前でアセンブリに署名する](../../../docs/framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md)  
 [Windows インストーラーの配置](http://msdn.microsoft.com/en-us/121be21b-b916-43e2-8f10-8b080516d2a0)
