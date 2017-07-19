---
title: "チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "カスタム コンポーネント, 追加 (ツールボックスに)"
  - "IToolboxService インターフェイス"
  - "ツールボックス [Windows フォーム], データの読み込み"
ms.assetid: 2fa1e3e8-6b9f-42b2-97c0-2be57444dba4
caps.latest.revision: 22
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 22
---
# チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定
現在開いているソリューションのプロジェクトで定義されたコンポーネントは、**\[ツールボックス\]** に自動的に表示され、独自の操作は必要ありません。  **\[ツールボックス\]** には、[Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/bd07835f-18a8-433e-bccc-7141f65263bb) を使用してカスタム コンポーネントを手動で設定することもできますが、**\[ツールボックス\]** は、ソリューションのビルド出力で次の特徴をすべて備えた項目に対応します。  
  
-   <xref:System.ComponentModel.IComponent> を実装する。  
  
-   <xref:System.ComponentModel.ToolboxItemAttribute> が `false` に設定されていない。  
  
-   <xref:System.ComponentModel.DesignTimeVisibleAttribute> が `false` に設定されていない。  
  
> [!NOTE]
>  **\[ツールボックス\]** は参照チェーンに従わないため、ソリューションのプロジェクトで構築されていない項目は表示されません。  
  
 このチュートリアルでは、構築されたカスタム コンポーネントが **\[ツールボックス\]** にどのように自動表示されるかについて説明します。  このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォーム プロジェクトの作成  
  
-   カスタム コンポーネントの作成  
  
-   カスタム コンポーネントのインスタンスの作成  
  
-   カスタム コンポーネントのアンロードと再読み込み  
  
 このチュートリアルでは最終的に、作成したコンポーネントが **\[ツールボックス\]** に読み込まれていることを確認します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### プロジェクトを作成するには  
  
1.  `ToolboxExample` という名前の Windows ベース アプリケーション プロジェクトを作成します。  
  
     詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  プロジェクトに新しいコンポーネントを追加します。  このコンポーネントに「`DemoComponent`」という名前を付けます。  
  
     詳細については、「[NIB:How to: Add New Project Items](http://msdn.microsoft.com/ja-jp/63d3e16b-de6e-4bb5-a0e3-ecec762201ce)」を参照してください。  
  
3.  プロジェクトをビルドします。  
  
4.  **\[ツール\]** メニューの **\[オプション\]** 項目をクリックします。  **\[Windows フォーム デザイナー\]** 項目の **\[全般\]** をクリックし、**\[AutoToolboxPopulate\]** オプションが **\[True\]** に設定されていることを確認します。  
  
## カスタム コンポーネントのインスタンスの作成  
 次に、カスタム コンポーネントのインスタンスをフォームで作成します。  **\[ツールボックス\]** は新しいコンポーネントに自動的に対応するため、これは、他のコンポーネントやコントロールを作成するのと同じように簡単です。  
  
#### カスタム コンポーネントのインスタンスを作成するには  
  
1.  プロジェクトのフォームを**フォーム デザイナー**で開きます。  
  
2.  **\[ツールボックス\]** で、**\[ToolboxExample コンポーネント\]** という新しいタブをクリックします。  
  
     このタブをクリックすると、**\[DemoComponent\]** が表示されます。  
  
    > [!NOTE]
    >  パフォーマンス上の理由により、**\[ツールボックス\]** の自動設定領域のコンポーネントはカスタム ビットマップを表示せず、<xref:System.Drawing.ToolboxBitmapAttribute> はサポートされません。  カスタム コンポーネントのアイコンを **\[ツールボックス\]** に表示するには、**\[ツールボックス アイテムの選択\]** ダイアログ ボックスを使用してコンポーネントを読み込みます。  
  
3.  コンポーネントをフォームにドラッグします。  
  
     コンポーネントのインスタンスが作成され、**\[コンポーネント トレイ\]** に追加されます。  
  
## カスタム コンポーネントのアンロードと再読み込み  
 **\[ツールボックス\]** は、読み込まれた各プロジェクトのコンポーネントに対応し、プロジェクトがアンロードされると、プロジェクトのコンポーネントへの参照が削除されます。  
  
#### ツールボックスに対するコンポーネントのアンロードと再読み込みの影響を確認するには  
  
1.  プロジェクトをソリューションからアンロードします。  
  
     プロジェクトのアンロードの詳細については、「[NIB:How to: Unload and Reload Projects](http://msdn.microsoft.com/ja-jp/abc0155b-8fcb-4ffc-95b6-698518a7100b)」を参照してください。  保存するかどうかを確認するダイアログ ボックスが表示された場合は、**\[はい\]** をクリックします。  
  
2.  ソリューションに新しい **Windows アプリケーション** プロジェクトを追加します。  **デザイナー**でフォームを開きます。  
  
     前のプロジェクトの **\[ToolboxExample コンポーネント\]** タブは削除されています。  
  
3.  `ToolboxExample` プロジェクトを再読み込みします。  
  
     **\[ToolboxExample コンポーネント\]** タブが再表示されます。  
  
## 次の手順  
 このチュートリアルでは、**\[ツールボックス\]** がプロジェクトのコンポーネントに対応することを説明してきましたが、**\[ツールボックス\]** は、コントロールにも対応します。  コントロール プロジェクトをソリューションに追加および削除して、独自のカスタム コントロールについても確認してみてください。  
  
## 参照  
 [General, Windows Forms Designer, Options Dialog Box](http://msdn.microsoft.com/ja-jp/8dd170af-72f0-4212-b04b-034ceee92834)   
 [How to: Manipulate Toolbox Tabs](http://msdn.microsoft.com/ja-jp/21285050-cadd-455a-b1f5-a2289a89c4db)   
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [Windows フォームへのコントロールの追加](../../../../docs/framework/winforms/controls/putting-controls-on-windows-forms.md)