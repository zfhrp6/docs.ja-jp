---
title: "方法: インストールされている .NET Framework の更新プログラムを確認する | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- updates, determining for .NET Framework
- .NET Framework, determining updates
ms.assetid: 53c7b5f7-d47a-402a-b194-7244a696a88b
caps.latest.revision: 6
author: mairaw
ms.author: mairaw
manager: wpickett
ms.translationtype: Human Translation
ms.sourcegitcommit: dc1c456c71efb3cc6e60a8fdc77384e65975f110
ms.openlocfilehash: 6237bdaf1d12743bee71633acf8cef69c21b414e
ms.contentlocale: ja-jp
ms.lasthandoff: 05/15/2017

---
# <a name="how-to-determine-which-net-framework-updates-are-installed"></a>方法 : インストールされている .NET Framework の更新プログラムを確認する
コンピューターにインストールされている .NET Framework のバージョンごとのインストール済みの更新プログラムは、Windows レジストリに一覧表示されます。 レジストリ エディター (regedit.exe) を使用して、この情報を表示することができます。  
  
 レジストリ エディターでは、各バージョンの .NET Framework バージョンとインストールされている更新プログラムが別々のサブキーに格納されます。 インストールされているバージョン番号を検出する方法については、「[方法: インストールされている .NET Framework バージョンを確認する](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)」を参照してください。 .NET Framework をインストールする方法については、[インストール ガイド](../../../docs/framework/install/guide-for-developers.md)を参照してください。  
  
### <a name="to-find-installed-updates"></a>インストールされている更新プログラムを確認するには  
  
1.  プログラム **regedit.exe** を開きます。 Windows 8 以降の場合、スタート画面を開き、名前を入力します。 それより前のバージョンの Windows では、**[スタート]** メニューの **[ファイル名を指定して実行]** を選択し、**[開く]** ボックスに **regedit.exe** と入力します。  
  
     regedit.exe を実行するには、管理特権が必要です。  
  
2.  レジストリ エディターで、次のサブキーを開きます。  
  
     HKEY_LOCAL_MACHINE\SOFTWARE\Wow6432Node\Microsoft\Updates  
  
     インストールされている更新プログラムは、適用された .NET Framework バージョンを識別するサブキーの下に一覧表示されています。 各更新プログラムは、サポート技術情報の (KB) 番号で識別されます。  
  
## <a name="example"></a>例  
 次のコードは、プログラミングによってコンピューターにインストールされている .NET Framework の更新プログラムを判断します。 この例を実行するには、管理特権が必要です。  
  
 [!code-csharp[ListUpdates#1](../../../samples/snippets/csharp/VS_Snippets_CLR/listupdates/cs/program.cs#1)] [!code-vb[ListUpdates#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/listupdates/vb/program.vb#1)]  
  
 この例では次のような出力が生成されます。  
  
```  
  
Microsoft .NET Framework 3.5 SP1  
  KB953595  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB953595)  
  SP1  
    KB2657424  Security Update for Microsoft .NET Framework 3.5 SP1 (KB2657424)  
    KB958484  Hotfix for Microsoft .NET Framework 3.5 SP1 (KB958484)  
    KB963707  Update for Microsoft .NET Framework 3.5 SP1 (KB963707)  
Microsoft .NET Framework 4 Client Profile  
  KB2160841  Security Update for Microsoft .NET Framework 4 Client Profile (KB2160841)  
  KB2446708  Security Update for Microsoft .NET Framework 4 Client Profile (KB2446708)  
  KB2468871  Update for Microsoft .NET Framework 4 Client Profile (KB2468871)  
  KB2478663  Security Update for Microsoft .NET Framework 4 Client Profile (KB2478663)  
  KB2518870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2518870)  
  KB2533523  Update for Microsoft .NET Framework 4 Client Profile (KB2533523)  
  KB2539636  Security Update for Microsoft .NET Framework 4 Client Profile (KB2539636)  
  KB2572078  Security Update for Microsoft .NET Framework 4 Client Profile (KB2572078)  
  KB2633870  Security Update for Microsoft .NET Framework 4 Client Profile (KB2633870)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Client Profile (KB2656351)  
Microsoft .NET Framework 4 Extended  
  KB2416472  Security Update for Microsoft .NET Framework 4 Extended (KB2416472)  
  KB2468871  Update for Microsoft .NET Framework 4 Extended (KB2468871)  
  KB2487367  Security Update for Microsoft .NET Framework 4 Extended (KB2487367)  
  KB2533523  Update for Microsoft .NET Framework 4 Extended (KB2533523)  
  KB2656351  Security Update for Microsoft .NET Framework 4 Extended (KB2656351)  
  
```  
  
## <a name="see-also"></a>関連項目  
 [方法 : インストールされている .NET Framework バージョンを確認する](../../../docs/framework/migration-guide/how-to-determine-which-versions-are-installed.md)   
 [インストール ガイド](../../../docs/framework/install/guide-for-developers.md)   
 [バージョンおよび依存関係](../../../docs/framework/migration-guide/versions-and-dependencies.md)

