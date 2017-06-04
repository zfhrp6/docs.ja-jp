---
title: "How to: Create a LINQ to DataSet Project In Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# How to: Create a LINQ to DataSet Project In Visual Studio
別の種類の [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] プロジェクトでは、特定のインポートされる名前空間 \(Visual Basic\) または `using` ディレクティブ \(C\#\) および参照が必要です。  最小要件は、System.Core.dll への参照と、<xref:System.Linq> の `using` ディレクティブです。  既定では、これらは新しい [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] プロジェクトを作成した場合に提供されます。  また、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] では、System.Data.dll および System.Data.DataSetExtensions.dll への参照と、`Imports` \(Visual Basic\) または `using` \(C\#\) ディレクティブも必要です。  
  
 以前のバージョンの Visual Studio のプロジェクトをアップグレードする場合、これらの LINQ 関連の参照を手動で追加する必要がある場合があります。  さらに、.NET Framework バージョン 3.5 をプロジェクトのターゲットとして手動で設定する必要がある場合があります。  
  
> [!NOTE]
>  コマンド プロンプトからビルドする場合、`drive`**:**\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.5 内の LINQ に関連する DLL を手動で参照する必要があります。  
  
### .NET Framework 3.5 をターゲットとして設定するには  
  
1.  [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] で、新しい Visual Basic または C\# プロジェクトを作成します。または、Visual Studio 2005 で作成されている Visual Basic または C\# プロジェクトを開き、指示に従って [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] プロジェクトに変換します。  
  
2.  C\# プロジェクトの場合は、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
    1.  **\[アプリケーション\]** プロパティ ページで、**\[ターゲット フレームワーク\]** ボックスの一覧から \[.NET Framework 3.5\] を選択します。  
  
3.  Visual Basic プロジェクトの場合は、**\[プロジェクト\]** メニューの **\[プロパティ\]** をクリックします。  
  
    1.  **\[コンパイル\]** プロパティ ページで、**\[詳細コンパイル オプション\]** をクリックし、**\[ターゲット フレームワーク \(すべての構成\)\]** ボックスの一覧から \[.NET Framework 3.5\] を選択します。  
  
4.  **\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックします。**\[.NET\]** タブをクリックし、下方向にスクロールし、**\[System.Core\]** をクリックします。最後に、**\[OK\]** をクリックします。  
  
5.  ソース コード ファイルまたはプロジェクトに <xref:System.Linq> の `using` ディレクティブまたはインポートされる名前空間を追加します。  
  
     詳細については、「[using ディレクティブ](../Topic/using%20Directive%20\(C%23%20Reference\).md)」または「[方法 : インポートした名前空間を追加または削除する \(Visual Basic\)](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20\(Visual%20Basic\).md)」を参照してください。  
  
### LINQ to DataSet 機能を有効にするには  
  
1.  必要に応じて、このトピックの前の方で説明した手順に従って、System.Core.dll への参照および System.Linq の `using` ディレクティブまたはインポートされる名前空間を追加します。  
  
2.  C\# または Visual Basic で、**\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックします。  
  
3.  **\[参照の追加\]** ダイアログ ボックスで、**\[.NET\]** タブが前面にない場合はこれをクリックします。  下方向にスクロールし、**\[System.Data\]** と **\[System.Data.DataSetExtensions\]** をクリックします。  **\[OK\]** をクリックします。  
  
4.  ソース コード ファイルまたはプロジェクトに <xref:System.Data> の `using` ディレクティブまたはインポートされる名前空間を追加します。  詳細については、「[using ディレクティブ](../Topic/using%20Directive%20\(C%23%20Reference\).md)」または「[方法 : インポートした名前空間を追加または削除する \(Visual Basic\)](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20\(Visual%20Basic\).md)」を参照してください。  
  
5.  LINQ to Dataset 機能を使用するために、System.Data.DataSetExtensions.dll への参照を追加します。  System.Data.dll への参照が追加されていない場合はこれを追加します。  
  
6.  オプションで、データベースにどのように接続するかに合わせて、`System.Data.Common` または `System.Data.SqlClient` の `using` ディレクティブまたはインポートされる名前空間を追加します。  
  
## 参照  
 [Getting Started](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)   
 [Getting Started with LINQ](http://msdn.microsoft.com/ja-jp/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)