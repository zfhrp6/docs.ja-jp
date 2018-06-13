---
title: PrintDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- PrintDialog
helpviewer_keywords:
- Print dialog box [Windows Forms], displaying
- PrintDialog component [Windows Forms], about PrintDialog component
ms.assetid: 8327b8ac-1017-4b5e-a88b-fea9dd56999c
ms.openlocfilehash: 0b0e516364277133efc83e7324345ccea8328690
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535490"
---
# <a name="printdialog-component-overview-windows-forms"></a>PrintDialog コンポーネントの概要 (Windows フォーム)
Windows フォーム[PrintDialog](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)コンポーネントは、構成済みのダイアログ ボックスのプリンターを選択し、印刷するページの選択、Windows ベースのアプリケーションで他の印刷関連の設定を決定するために使用します。 独自のダイアログ ボックスを構成する代わりに、プリンターと印刷関連の設定の選択のための簡単なソリューションとして使用します。 ユーザーが自分のドキュメントの多くの部分を印刷を有効にすることができます。 すべてを印刷、選択したページ範囲、または選択した印刷します。 Windows の標準のダイアログ ボックスを使用して、ユーザーがすぐに慣れる基本的な機能を持つアプリケーションを作成します。 <xref:System.Windows.Forms.PrintDialog>コンポーネントが継承、<xref:System.Windows.Forms.CommonDialog>クラスです。  
  
## <a name="working-with-the-component"></a>コンポーネントの操作  
 使用して、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドを実行時に、ダイアログ ボックスを表示します。 このコンポーネントには、単一の印刷ジョブのいずれかに関連するプロパティ (<xref:System.Drawing.Printing.PrintDocument>クラス) または個々 のプリンターの設定 (<xref:System.Drawing.Printing.PrinterSettings>クラス)。 さらに、これらのいずれかには複数のプリンターで共有することがあります。  
  
 フォームに追加されたとき、<xref:System.Windows.Forms.PrintDialog>コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.PrintDialog>  
 [PrintDialog コンポーネント](../../../../docs/framework/winforms/controls/printdialog-component-windows-forms.md)
