---
title: FontDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- FontDialog
helpviewer_keywords:
- Font dialog box [Windows Forms], Windows Forms
- Font dialog box
- FontDialog component [Windows Forms], about FontDialog component
ms.assetid: daf46e57-1b4b-4b7a-bad0-b50ca7ba75dc
ms.openlocfilehash: 3a4707ffe471161988d0526ce0908b37299f3e07
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526879"
---
# <a name="fontdialog-component-overview-windows-forms"></a>FontDialog コンポーネントの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.FontDialog>コンポーネントは、構成済みのダイアログ ボックスは、これは、標準の Windows**フォント** ダイアログ ボックスを使用して、システムに現在インストールされているフォントを公開します。 独自のダイアログ ボックスを構成する代わりにフォントの選択の簡単な解決策として、Windows ベースのアプリケーション内で使用します。  
  
 既定では、ダイアログ ボックスに表示リスト ボックスのフォント、フォント スタイル、およびサイズです。取り消し線、下線; などの効果のチェック ボックススクリプトのドロップダウン リストフォントがどのように表示されるかのサンプルです。 (スクリプトは、特定のフォントで利用可能な異なる文字スクリプトなど、ヘブライ語や日本語)。表示するには、[フォント] ダイアログ ボックスを呼び出す、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドです。  
  
## <a name="key-properties"></a>キー プロパティ  
 コンポーネントが、その外観を構成するプロパティの数。 ダイアログ ボックスの選択項目を設定するプロパティは<xref:System.Windows.Forms.FontDialog.Font%2A>と<xref:System.Windows.Forms.FontDialog.Color%2A>です。 <xref:System.Windows.Forms.FontDialog.Font%2A>プロパティ設定のフォント、スタイル、サイズ、スクリプト、および影響です。 たとえば、`Arial, 10pt, style=Italic, Strikeout`です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.FontDialog>  
 [FontDialog コンポーネント](../../../../docs/framework/winforms/controls/fontdialog-component-windows-forms.md)
