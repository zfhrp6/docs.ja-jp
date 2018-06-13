---
title: DomainUpDown コントロール (Windows フォーム)
ms.date: 03/30/2017
helpviewer_keywords:
- DomainUpDown control [Windows Forms]
- spin button control [Windows Forms], up-down controls
- up-down controls
- spin button control
- up-down controls [Windows Forms], spin button controls
ms.assetid: fb7cf017-e931-4a95-9d21-8caee4ee122a
ms.openlocfilehash: c23f374f1ec9cab6e43b12d32b97c40533ac36cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527327"
---
# <a name="domainupdown-control-windows-forms"></a>DomainUpDown コントロール (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.DomainUpDown>コントロールよう組のボタンとテキスト ボックスの組み合わせの一覧を上または下に移動します。 コントロールは、表示し、選択肢の一覧から、テキスト文字列を設定します。 上下一覧内を移動するボタンをクリックして、上下の矢印キーを押すことによって、または、リスト内の項目に一致する文字列を入力して、ユーザーは、文字列を選択できます。 このコントロールの用途の 1 つでは、名前のアルファベット順に並べ替えられたリストから項目を選択するためです。 (一覧を並べ替えるには設定、<xref:System.Windows.Forms.DomainUpDown.Sorted%2A>プロパティを`true`)。このコントロールの機能は、リスト ボックスまたはコンボ ボックスによく似ていますが、非常に小さい領域を占有します。  
  
 コントロールのプロパティは<xref:System.Windows.Forms.DomainUpDown.Items%2A>、 <xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>、および<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>です。 <xref:System.Windows.Forms.DomainUpDown.Items%2A>プロパティには、文字列値を持つが、コントロールに表示されるオブジェクトの一覧が含まれています。 場合<xref:System.Windows.Forms.UpDownBase.ReadOnly%2A>に設定されている`false`コントロールは、ユーザーが型し、リスト内の値を内容と一致するテキストを自動的に完了します。 場合<xref:System.Windows.Forms.DomainUpDown.Wrap%2A>に設定されている`true`、スクロールの過去の最後の項目をクリックすると、一覧で、その逆の最初の項目。 コントロールの主要なメソッドは<xref:System.Windows.Forms.DomainUpDown.UpButton%2A>と<xref:System.Windows.Forms.DomainUpDown.DownButton%2A>です。  
  
 このコントロールには、テキスト文字列のみが表示されます。 数値を表示するコントロールを実行する場合に、使用、<xref:System.Windows.Forms.NumericUpDown>コントロール。 詳細については、次を参照してください。 [NumericUpDown コントロール](../../../../docs/framework/winforms/controls/numericupdown-control-windows-forms.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [DomainUpDown コントロールの概要](../../../../docs/framework/winforms/controls/domainupdown-control-overview-windows-forms.md)  
 一般的な概念が導入されています、<xref:System.Windows.Forms.DomainUpDown>コントロールを参照し、テキスト文字列の一覧から選択することができます。  
  
 [方法: Windows フォーム DomainUpDown コントロールにプログラムで項目を追加する](../../../../docs/framework/winforms/controls/how-to-add-items-to-windows-forms-domainupdown-controls-programmatically.md)  
 テキスト文字列を指定する方法について説明します、<xref:System.Windows.Forms.DomainUpDown>コントロールを表示する必要があります。  
  
 [方法: Windows フォームの DomainUpDown コントロールから項目を削除する](../../../../docs/framework/winforms/controls/how-to-remove-items-from-windows-forms-domainupdown-controls.md)  
 項目を削除する方法について説明します、<xref:System.Windows.Forms.DomainUpDown>コード内でコントロール。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.DomainUpDown>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.NumericUpDown>  
 このクラスについて説明し、すべてのメンバーへのリンクがあります.  
  
## <a name="related-sections"></a>関連項目  
 [Windows フォームで使用するコントロール](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 Windows フォーム コントロールの完全な一覧を、使用に関する情報リンクと共に提供します。
