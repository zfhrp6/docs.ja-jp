---
title: OpenFileDialog コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: a49298b2e2cc620ad95e2e0b601a2f49f6ff79d4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536079"
---
# <a name="openfiledialog-component-overview-windows-forms"></a>OpenFileDialog コンポーネントの概要 (Windows フォーム)
Windows フォームの <xref:System.Windows.Forms.OpenFileDialog> コンポーネントは、事前構成済みのダイアログ ボックスです。 これは、同じ**ファイルを開く** ダイアログ ボックスが、Windows オペレーティング システムによって公開されています。 これは、<xref:System.Windows.Forms.CommonDialog> クラスを継承しています。  
  
## <a name="using-this-component"></a>このコンポーネントを使用します。  
 簡易ソリューションとして、Windows ベースのアプリケーション内でこのコンポーネントを使用して、独自のダイアログ ボックスを構成する代わりにファイルを選択します。 Windows の標準のダイアログ ボックスを使用して、ユーザーがすぐに慣れる基本的な機能を持つアプリケーションを作成します。 ただし、ときに使用して、<xref:System.Windows.Forms.OpenFileDialog>コンポーネント、独自のファイルを開くロジックを記述する必要があります。  
  
 使用して、<xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>メソッドを実行時に、ダイアログ ボックスを表示します。 複数選択するためファイルにで開くことがユーザーを有効にすることができます、<xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>プロパティです。 また、使用することができます、<xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A>プロパティのかどうか ダイアログ ボックスで、読み取り専用 チェック ボックスが表示されます。 <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A>プロパティは読み取り専用チェック ボックスをオンになっているかどうかを示します。 最後に、<xref:System.Windows.Forms.FileDialog.Filter%2A>プロパティ設定の現在のファイル名フィルターの文字列 ダイアログ ボックスで、"ファイルの種類 ボックスに表示される選択肢を決定します。  
  
 フォームに追加されたとき、<xref:System.Windows.Forms.OpenFileDialog>コンポーネントは、Windows フォーム デザイナーの下部にあるトレイに表示されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [OpenFileDialog コンポーネント](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
