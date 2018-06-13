---
title: SaveFileDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- SaveFileDialog
helpviewer_keywords:
- Save File dialog box [Windows Forms], displaying
- SaveFileDialog component [Windows Forms], about SaveFileDialog
ms.assetid: be7a625f-46fd-4d06-9985-b613dcbf9bd2
ms.openlocfilehash: be5f70e2e8b0d5143ef387819689ce95564a72d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537448"
---
# <a name="savefiledialog-component-overview-windows-forms"></a>SaveFileDialog コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.SaveFileDialog> コンポーネントは、事前構成済みのダイアログ ボックスです。 標準と同じである**ファイルを保存** ダイアログ ボックスの Windows で使用します。 これは、<xref:System.Windows.Forms.CommonDialog> クラスを継承しています。  
  
## <a name="working-with-the-savefiledialog-component"></a>SaveFileDialog コンポーネントの操作  
 独自のダイアログ ボックスを構成する代わりにファイルを保存するユーザーを有効にするための簡易ソリューションとして使用します。 標準の Windows ダイアログ ボックスには、この証明書利用者で作成したアプリケーションの基本機能は、ユーザーにすぐに慣れるです。 ただし、ときに使用して、<xref:System.Windows.Forms.SaveFileDialog>コンポーネント、独自のファイルの保存ロジックを記述する必要があります。  
  
 使用することができます、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドを実行時に、ダイアログ ボックスを表示します。 読み取り/書き込みモードを使用してファイルを開くことができます、<xref:System.Windows.Forms.SaveFileDialog.OpenFile%2A>メソッドです。  
  
 フォームに追加されたとき、<xref:System.Windows.Forms.SaveFileDialog>コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.SaveFileDialog>  
 [SaveFileDialog コンポーネント](../../../../docs/framework/winforms/controls/savefiledialog-component-windows-forms.md)
