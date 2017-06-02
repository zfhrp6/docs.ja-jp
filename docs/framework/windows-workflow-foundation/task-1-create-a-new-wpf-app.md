---
title: "タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 270eaeba-9492-4532-af9f-403ce5c9935b
caps.latest.revision: 14
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 14
---
# タスク 1: 新しい Windows Presentation Foundation アプリケーションの作成
このタスクでは、WPF Application Visual Studio テンプレートを使用することによって、空の [!INCLUDE[avalon1](../../../includes/avalon1-md.md)] アプリケーションを作成し、適切な [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] ワークフロー アセンブリに参照を追加します。  
  
### WPF アプリケーション プロジェクトを作成するには  
  
1.  [!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] を開き、**\[ファイル\]** メニューの **\[新規作成\]** をポイントし、**\[プロジェクト\]** をクリックします。  
  
2.  **\[新しいプロジェクト\]** ダイアログ ボックスの左側にある **\[インストールされているテンプレート\]** ペインで、**\[Visual C\#\]** または **\[Visual Basic\]** を選択します。選択した言語が表示されない場合は、**\[他の言語\]** で探します。  
  
3.  **\[インストールされているテンプレート\]** ペインの **\[Windows\]** を選択します。  
  
4.  上部ペインにあるドロップダウン リスト ボックスで、既定値の **\[.NET Framework 4\]** が選択されていることを確認し、**\[WPF アプリケーション\]** を選択します。  
  
5.  ウィンドウの下部でプロジェクトの名前を **HostingApplication** に設定します。  
  
6.  ソリューションの名前を **RehostingTheDesigner** に設定します。  
  
7.  **\[OK\]** をクリックすると、アプリケーション プロジェクトが作成されます。[!INCLUDE[vs_current_short](../../../includes/vs-current-short-md.md)] によって、使用するアプリケーション用の基本的な WPF UI が作成され、適切な XAML と分離コード ファイルが含まれます。  
  
8.  **WorkflowModel** アセンブリへの参照を追加します。この場合、**ソリューション エクスプローラー**で **HostingApplication** プロジェクトを右クリックし、**\[参照の追加\]** をクリックします。  
  
9. **\[参照の追加\]** ダイアログ ボックスで、**\[.NET\]** タブをクリックし、Ctrl キーを押しながら次のアセンブリを選択して、**\[OK\]** をクリックします。  
  
    -   System.Activities  
  
    -   System.Activities.Presentation  
  
    -   System.Activities.Core.Presentation  
  
10. **\[OK\]** をクリックします。  
  
11. ワークフロー デザイナーのデザイン キャンバスをホストする方法については、「[タスク 2: ワークフロー デザイナーのホスティング](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md)」を参照してください。  
  
## 参照  
 [ワークフロー デザイナーのホスト変更](../../../docs/framework/windows-workflow-foundation//rehosting-the-workflow-designer.md)   
 [タスク 2: ワークフロー デザイナーのホスティング](../../../docs/framework/windows-workflow-foundation//task-2-host-the-workflow-designer.md)