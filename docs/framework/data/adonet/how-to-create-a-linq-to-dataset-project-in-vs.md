---
title: "方法 : Visual Studio で LINQ to DataSet プロジェクトを作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 6710d3e9bf52ff10ee8dd545161f0858001f2c40
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>方法 : Visual Studio で LINQ to DataSet プロジェクトを作成する
別の種類の [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] プロジェクトでは、特定のインポートされる名前空間 (Visual Basic) または `using` ディレクティブ (C#) および参照が必要です。 最小要件は、System.Core.dll への参照と、`using` の <xref:System.Linq> ディレクティブです。 既定では、これらは新しい [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)] プロジェクトを作成した場合に提供されます。 また、[!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] では、System.Data.dll および System.Data.DataSetExtensions.dll への参照と、`Imports` (Visual Basic) または `using` (C#) ディレクティブも必要です。  
  
 以前のバージョンの Visual Studio のプロジェクトをアップグレードする場合、これらの LINQ 関連の参照を手動で追加する必要がある場合があります。 さらに、.NET Framework バージョン 3.5 をプロジェクトのターゲットとして手動で設定する必要がある場合があります。  
  
> [!NOTE]
>  コマンド プロンプトから構築する場合での LINQ に関連する Dll を手動で参照する必要があります`drive` **:**\Program Files\Reference Assemblies\Microsoft\Framework\v3.5 です。  
  
### <a name="to-target-the-net-framework-35"></a>.NET Framework 3.5 をターゲットとして設定するには  
  
1.  [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] で、新しい Visual Basic または C# プロジェクトを作成します。 または、Visual Studio 2005 で作成されている Visual Basic または C# プロジェクトを開き、指示に従って [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] プロジェクトに変換します。  
  
2.  C# プロジェクトをクリックして、**プロジェクト** メニューをクリックして**プロパティ**です。  
  
    1.  **アプリケーション**プロパティ] ページで、[.NET Framework 3.5、**ターゲット フレームワーク**ドロップダウン リスト。  
  
3.  Visual Basic プロジェクトをクリックして、**プロジェクト** メニューをクリックして**プロパティ**です。  
  
    1.  **コンパイル**プロパティ ページで、をクリックして**詳細コンパイル オプション**で .NET Framework 3.5 をクリックして、**ターゲット フレームワーク (すべての構成)**ドロップダウン リスト。  
  
4.  **プロジェクト** メニューのをクリックして**参照の追加**をクリックして、 **.NET**  タブで、下方向にスクロール**System.Core**をクリックし、 をクリックして**Ok**です。  
  
5.  ソース コード ファイルまたはプロジェクトに `using` の <xref:System.Linq> ディレクティブまたはインポートされる名前空間を追加します。  
  
     詳細については、次を参照してください。[ディレクティブを使用して](~/docs/csharp/language-reference/keywords/using-directive.md)または[する方法: 追加またはインポートされた名前空間 (Visual Basic) を削除する](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)です。  
  
### <a name="to-enable-linq-to-dataset-functionality"></a>LINQ to DataSet 機能を有効にするには  
  
1.  必要に応じて、このトピックの前の方で説明した手順に従って、System.Core.dll への参照および System.Linq の `using` ディレクティブまたはインポートされる名前空間を追加します。  
  
2.  C# または Visual Basic の場合をクリックして、**プロジェクト** メニューをクリックして**参照の追加**です。  
  
3.  **参照の追加** ダイアログ ボックスをクリックして、 **.NET**タブが前面にない場合。 下方向にスクロール**System.Data**と**System.Data.DataSetExtensions**にをクリックします。 クリックして、 **OK**ボタンをクリックします。  
  
4.  ソース コード ファイルまたはプロジェクトに `using` の <xref:System.Data> ディレクティブまたはインポートされる名前空間を追加します。 詳細については、次を参照してください。[ディレクティブを使用して](~/docs/csharp/language-reference/keywords/using-directive.md)または[する方法: 追加またはインポートされた名前空間 (Visual Basic) を削除する](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic)です。  
  
5.  LINQ to Dataset 機能を使用するために、System.Data.DataSetExtensions.dll への参照を追加します。 System.Data.dll への参照が追加されていない場合はこれを追加します。  
  
6.  オプションで、データベースにどのように接続するかに合わせて、`using` または `System.Data.Common` の `System.Data.SqlClient` ディレクティブまたはインポートされる名前空間を追加します。  
  
## <a name="see-also"></a>参照  
 [はじめに](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [はじめに (LINQ について)](http://msdn.microsoft.com/en-us/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
