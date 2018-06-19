---
title: PageSetupDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- PageSetupDialog
helpviewer_keywords:
- Page Setup dialog box [Windows Forms], displaying
- PageSetupDialog component
ms.assetid: 791caacb-a5ca-4fca-bad9-1a5721ad697c
ms.openlocfilehash: 4e7b4548f5a178ed7b819dbc2edc37bb95e3e0f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33534226"
---
# <a name="pagesetupdialog-component-overview-windows-forms"></a>PageSetupDialog コンポーネントの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.PageSetupDialog>コンポーネントは、構成済みのダイアログ ボックスが Windows ベースのアプリケーションで印刷ページの詳細を設定するために使用します。 独自のダイアログ ボックスを構成する代わりに、ページの基本設定を設定するのにユーザーの簡単な解決策として、Windows ベース アプリケーションの中で使用します。 ユーザーに境界線と余白の調整、ヘッダーとフッター、および縦または横方向の設定を有効にすることができます。 Windows の標準のダイアログ ボックスを使用して、ユーザーがすぐに慣れる基本的な機能を持つアプリケーションを作成します。  
  
## <a name="key-properties-and-methods"></a>キー プロパティとメソッド  
 使用して、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドを実行時に、ダイアログ ボックスを表示します。 このコンポーネントには 1 つのページのいずれかに関連するプロパティを設定できます (<xref:System.Drawing.Printing.PrintDocument>クラス)、または任意の文書 (<xref:System.Drawing.Printing.PageSettings>クラス)。 さらに、<xref:System.Windows.Forms.PageSetupDialog>に格納されている特定のプリンター設定を確認するコンポーネントを使用することができます、<xref:System.Drawing.Printing.PrinterSettings>クラスです。  
  
 フォームに追加されたとき、<xref:System.Windows.Forms.PageSetupDialog>コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.PageSetupDialog>  
 [PageSetupDialog コンポーネント](../../../../docs/framework/winforms/controls/pagesetupdialog-component-windows-forms.md)
