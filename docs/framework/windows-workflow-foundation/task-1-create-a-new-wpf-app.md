---
title: 'タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成'
ms.date: 03/30/2017
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
ms.openlocfilehash: 5576d6f893aa405d454758387334b85a473b0c73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517950"
---
# <a name="task-1-create-a-new-windows-presentation-foundation-application"></a>タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成
このタスクでは、WPF Application Visual Studio テンプレートを使用して空の Windows Presentation Foundation (WPF) アプリケーションを作成し、適切な参照を追加[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]ワークフロー アセンブリ。  
  
### <a name="to-create-the-wpf-application-project"></a>WPF アプリケーション プロジェクトを作成するには  
  
1.  Visual Studio を開き、および、**ファイル** メニューのをポイント**新規**、順にクリック**プロジェクト**です。  
  
2.  **新しいプロジェクト** ダイアログ ボックスで、いずれかを選択**Visual c#** または**Visual Basic**から、**インストールされたテンプレート**の左側にあるウィンドウボックス。 任意の言語が表示されない場合は、下にある検索**他の言語**します。  
  
3.  選択**Windows**で、**インストールされたテンプレート**ウィンドウです。  
  
4.  上部のペインにいることを確認 (既定値) **.NET Framework 4**が選択されてドロップダウン リスト ボックスで、 **WPF アプリケーション**です。  
  
5.  プロジェクトの名前を設定**HostingApplication**ウィンドウの下部にあります。  
  
6.  ソリューション名を設定します**RehostingTheDesigner**です。  
  
7.  をクリックして**OK**アプリケーション プロジェクトを作成します。 Visual Studio では、アプリケーションの基本的な WPF UI を作成し、適切な XAML と分離コード ファイルが含まれています。  
  
8.  参照を追加**WorkflowModel**アセンブリ。 これを行うで**ソリューション エクスプ ローラー**を右クリックし、 **HostingApplication**プロジェクトし、選択**参照の追加**です。  
  
9. **参照の追加**ダイアログ ボックスで、をクリックして、 **.NET**  タブ、CTRL キーを押しながら、次のアセンブリを選択し、をクリックして**OK**:  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. **[OK]** をクリックします。  
  
11. 参照してください[タスク 2: ワークフロー デザイナーのホスティング](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)をワークフロー デザイナーのデザイン キャンバスをホストする方法を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [ワークフロー デザイナーのホスト変更](../../../docs/framework/windows-workflow-foundation/rehosting-the-workflow-designer.md)  
 [タスク 2: ワークフロー デザイナーのホスティング](../../../docs/framework/windows-workflow-foundation/task-2-host-the-workflow-designer.md)
