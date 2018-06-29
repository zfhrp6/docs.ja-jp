---
title: '方法 : Windows フォーム アプリケーションでのフォント パターンの変更に応答する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 2451885c673515eb6690b0784fd5bd22de629209
ms.sourcegitcommit: 9e18e4a18284ae9e54c515e30d019c0bbff9cd37
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/28/2018
ms.locfileid: "37071147"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>方法 : Windows フォーム アプリケーションでのフォント パターンの変更に応答する
Windows オペレーティング システムでは、ユーザーが表示される既定のフォントのサイズを変更するシステム全体のフォント設定を変更できます。 これらのフォント設定を変更するは、視覚に障害を画面上のテキストを読み取るより大きい型を必要なユーザーに重要です。 フォント パターンが変更されるたびに、フォームとに含まれるすべてのテキストのサイズを増減してこれらの変更に反応する Windows フォーム アプリケーションを調整することができます。 フォームをフォント サイズの変化に動的に対応する場合は、フォームにコードを追加できます。  
  
 通常、Windows フォームで使用される既定のフォントは、によって返される、フォント、<xref:Microsoft.Win32>名前空間の呼び出し`GetStockObject(DEFAULT_GUI_FONT)`です。 この呼び出しによって返されるフォントは、画面の解像度が変更されたときにのみ変更します。 既定のフォントを次の手順に示すように、コードを変更する必要があります<xref:System.Drawing.SystemFonts.IconTitleFont%2A>フォントのサイズ変更に応答します。  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>デスクトップのフォントを使用し、フォント パターンの変更に応答するには  
  
1.  フォームを作成し、必要なコントロールを追加します。 詳細については、次を参照してください。[する方法: コマンドラインから Windows フォーム アプリケーションを作成する](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md)と[Windows フォームで使用するコントロール](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)です。  
  
2.  参照を追加、<xref:Microsoft.Win32>名前空間をコードにします。  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  必要なイベント ハンドラーをフックするために、フォームの使用中の既定のフォントを変更するのには、フォームのコンス トラクターに次のコードを追加します。  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  ハンドラーを実装、<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>自動的に拡張するフォームの原因となるイベントと、<xref:Microsoft.Win32.UserPreferenceCategory.Window>カテゴリの変更。  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  最後に、ハンドラーを実装する、<xref:System.Windows.Forms.Form.FormClosing>の関連付けを解除するイベント、<xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>イベント ハンドラー。  
  
     > [!IMPORTANT]
     > このコードを含めないと、アプリケーションでメモリ リークが発生します。  
  
     [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6.  コードをコンパイルして実行します。  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Windows XP でのフォント パターンを手動で変更するには  
  
1.  Windows フォーム アプリケーションの実行中に Windows のデスクトップを右クリックして選択**プロパティ**ショートカット メニューからです。  
  
2.  **表示プロパティ**ダイアログ ボックスで、をクリックして、**外観**タブです。  
  
3.  **フォント サイズ**ドロップダウン リスト ボックスで、新しいフォントのサイズを選択します。  
  
     フォームがデスクトップのフォント パターンの実行時の変更に対応することがわかります。 間、ユーザーが変更されたとき**標準**、**大きいフォント**、および**特大フォント**フォームのフォントを変更し、スケールが適切です。  
  
## <a name="example"></a>例  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 このコード例では constructer にはへの呼び出しが含まれています`InitializeComponent`、これは Visual Studio で新しい Windows フォーム プロジェクトを作成するときに定義されています。 コマンドラインでアプリケーションを構築する場合は、次のコード行を削除します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 [Windows フォームにおける自動スケーリング](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
