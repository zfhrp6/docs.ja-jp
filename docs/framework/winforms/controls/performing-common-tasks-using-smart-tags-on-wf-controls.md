---
title: "チュートリアル : Windows フォーム コントロールのスマート タグを使用した共通タスクの実行 | Microsoft Docs"
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
  - "デザイナー アクション"
  - "DesignerAction オブジェクト モデル"
  - "スマート タグ"
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# チュートリアル : Windows フォーム コントロールのスマート タグを使用した共通タスクの実行
Windows フォーム アプリケーションのフォームやコントロールを構成するときは、繰り返し実行するタスクが数多くあります。  そのような共通タスクには、次のようなものがあります。  
  
-   <xref:System.Windows.Forms.TabControl> へのタブの追加または削除  
  
-   親コントロールへのコントロールのドッキング  
  
-   <xref:System.Windows.Forms.SplitContainer> コントロールの方向の変更  
  
 開発をスピードアップするために、多くのコントロールにはスマート タグが用意されています。スマート タグは、上記のような共通タスクをデザイン時に単一の操作で実行できるようにする状況依存のメニューです。  これらのタスクは、*スマートタグ動詞*と呼ばれています。  
  
 スマート タグは、デザイナーでコントロール インスタンスが有効な間、コントロール インスタンスに表示されいつでも使用できます。  
  
 このチュートリアルでは、以下のタスクを行います。  
  
-   Windows フォーム プロジェクトの作成  
  
-   スマート タグの使用  
  
-   スマート タグの有効化と無効化  
  
 ここでは、これらの重要なレイアウト機能が果たす役割について理解します。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
## プロジェクトの作成  
 最初にプロジェクトを作成し、フォームを設定します。  
  
#### プロジェクトを作成するには  
  
1.  "SmartTagsExample" という名前の Windows ベース アプリケーション プロジェクトを作成します。  詳細については、「[How to: Create a Windows Application Project](http://msdn.microsoft.com/ja-jp/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。  
  
2.  **Windows フォーム デザイナー**でフォームを選択します。  
  
## スマート タグの使用  
 スマート タグを提供するコントロールでは、デザイン時にいつでもスマート タグを使用できます。  
  
#### スマート タグを使用するには  
  
1.  **ツールボックス**の <xref:System.Windows.Forms.TabControl> コントロールをフォームにドラッグします。  スマート タグ グリフ \(![スマート タグ グリフ](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.png "VS\_WinFormSmtTagGlyph")\) が <xref:System.Windows.Forms.TabControl> の横に表示されます。  
  
2.  スマート タグ グリフをクリックします。  グリフの横に表示されるショートカット メニューの **\[タブの追加\]** をクリックします。  新しいタブ ページが <xref:System.Windows.Forms.TabControl> に追加されることを確認してください。  
  
3.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.TableLayoutPanel> コントロールをドラッグします。  
  
4.  スマート タグ グリフをクリックします。  グリフの横に表示されるショートカット メニューの **\[列の追加\]** をクリックします。  新しい列が <xref:System.Windows.Forms.TableLayoutPanel> コントロールに追加されることを確認してください。  
  
5.  **ツールボックス**からフォームに、<xref:System.Windows.Forms.SplitContainer> コントロールをドラッグします。  
  
6.  スマート タグ グリフをクリックします。  グリフの横に表示されるショートカット メニューの **\[上下分割の方向\]** をクリックします。  <xref:System.Windows.Forms.SplitContainer> コントロールの分割バーが横向きになったことを確認してください。  
  
## 参照  
 <xref:System.Windows.Forms.TextBox>   
 <xref:System.Windows.Forms.TabControl>   
 <xref:System.Windows.Forms.SplitContainer>   
 <xref:System.ComponentModel.Design.DesignerActionList>   
 [Walkthrough: Adding Smart Tags to a Windows Forms Component](../Topic/Walkthrough:%20Adding%20Smart%20Tags%20to%20a%20Windows%20Forms%20Component.md)