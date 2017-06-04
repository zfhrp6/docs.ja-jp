---
title: "方法 : Windows フォーム アプリケーションでのフォント パターンの変更に応答する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "Windows フォーム, フォント パターンの変更"
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : Windows フォーム アプリケーションでのフォント パターンの変更に応答する
Windows オペレーティング システムでは、システム全体のフォント設定を変更して、既定のフォントの表示サイズを大きくしたり、小さくしたりできます。  このようなフォント設定の変更は、視覚障害があり、画面上のテキストを読み取る際に比較的大きめの活字を必要とするユーザーにとって重要です。  Windows フォーム アプリケーションを、このような変更に合わせて調整するには、フォント パターンが変更されたときにフォームとフォームに含まれるすべてのテキストのサイズを拡大または縮小します。  フォント サイズの変更にフォームが動的に対応するようにする場合は、フォームにコードを追加します。  
  
 通常、Windows フォームで使用される既定のフォントは、<xref:Microsoft.Win32> 名前空間での `GetStockObject(DEFAULT_GUI_FONT)` への呼び出しで返されたフォントです。  この呼び出しで返されたフォントは、画面の解像度を変更したときにのみ変更されます。  次の手順に示すように、フォント サイズの変更に応答するには、コードによって既定のフォントを <xref:System.Drawing.SystemFonts.IconTitleFont%2A> に変更する必要があります。  
  
### デスクトップ フォントを使用して、フォント パターンの変更に応答するには  
  
1.  フォームを作成し、必要なコントロールを追加します。  詳細については、「[方法 : コマンド ラインから Windows フォーム アプリケーションを作成する](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md)」および「[Windows フォームで使用するコントロール](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)」を参照してください。  
  
2.  <xref:Microsoft.Win32> 名前空間への参照をコードに追加します。  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  必要なイベント ハンドラーをフックし、フォームで使用する既定のフォントを変更するために、次のコードをフォームのコンストラクターに追加します。  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> イベントのハンドラーを実装します。これにより、<xref:Microsoft.Win32.UserPreferenceCategory> カテゴリが変更されたときにフォームが自動的にスケーリングされます。  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  最後に、<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> イベント ハンドラーをデタッチする、<xref:System.Windows.Forms.Form.FormClosing> イベントのハンドラーを実装します。  
  
> [!IMPORTANT]
>  このコードを追加しないと、アプリケーションでメモリ リークが発生します。  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  コードをコンパイルして実行します。  
  
### Windows XP でフォント パターンを手動で変更するには  
  
1.  Windows フォーム アプリケーションを実行しているときに Windows のデスクトップを右クリックし、ショートカット メニューの **\[プロパティ\]** をクリックします。  
  
2.  **\[画面のプロパティ\]** ダイアログ ボックスの **\[デザイン\]** タブをクリックします。  
  
3.  **\[フォント サイズ\]** ボックスで、新しいフォント サイズを選択します。  
  
     フォームは、デスクトップ フォント パターンの実行時の変更に対応します。  ユーザーが **\[標準\]**、**\[大\]**、または **\[特大\]** のいずれかに変更すると、フォームのフォントとスケールが適切に変更されます。  
  
## 使用例  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 次のコード例に示されているコンストラクターには、Visual Studio で新しい Windows フォームを作成するときに定義される `InitializeComponent` への呼び出しが含まれています。  アプリケーションをコマンド ラインで作成する場合は、このコード行を削除してください。  
  
## 参照  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>   
 [Windows フォームにおける自動スケーリング](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)