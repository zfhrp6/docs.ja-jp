---
title: ErrorProvider コンポーネントの概要 (Windows フォーム)
ms.date: 03/30/2017
f1_keywords:
- ErrorProvider
helpviewer_keywords:
- errors [Windows Forms], displaying to users
- error messages [Windows Forms], displaying
- ErrorProvider component [Windows Forms], about ErrorProvider component
ms.assetid: ced189f2-b5c8-46a7-a6f1-37f5af95dc99
ms.openlocfilehash: 2272220917f2d5adf15f1ba84a5d4c3d0ec07165
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33528887"
---
# <a name="errorprovider-component-overview-windows-forms"></a>ErrorProvider コンポーネントの概要 (Windows フォーム)
Windows フォーム[ErrorProvider](../../../../docs/framework/winforms/controls/errorprovider-component-windows-forms.md)コンポーネントは、フォームまたはコントロールのユーザー入力の検証に使用します。 通常、フォーム上のユーザー入力の検証またはデータセット内のエラーを表示すると組み合わせて使用されます。 エラー プロバイダーでは、エラー メッセージを表示するメッセージ ボックスより優れた選択肢をメッセージ ボックスが閉じられた後は、エラー メッセージが表示されないためです。 <xref:System.Windows.Forms.ErrorProvider>コンポーネントには、エラー アイコンが表示されます (![ErrorProvider アイコン](../../../../docs/framework/winforms/controls/media/vberrorprovidericon.gif "vbErrorProviderIcon"))、テキスト ボックスは、ユーザーが上にマウス ポインターを置いたときなど、関連するコントロールの横に、エラー アイコン、ツールヒントが表示されます、エラー メッセージ文字列を表示します。  
  
## <a name="key-properties"></a>キー プロパティ  
 <xref:System.Windows.Forms.ErrorProvider>コンポーネントのプロパティは<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>、 <xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>、および<xref:System.Windows.Forms.ErrorProvider.Icon%2A>です。 使用する場合<xref:System.Windows.Forms.ErrorProvider>コンポーネント、データ バインド コントロールを<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>プロパティは、エラー アイコンをフォームに表示する対象のコンポーネントの順序で適切なコンテナー (通常は Windows フォーム) に設定する必要があります。 デザイナーでコンポーネントを追加すると、<xref:System.Windows.Forms.ErrorProvider.ContainerControl%2A>プロパティが対象のフォームに設定されている場合はコード内にコントロールを追加すると、設定することは必要があります自分でします。  
  
 <xref:System.Windows.Forms.ErrorProvider.Icon%2A>プロパティは、既定ではなく独自のエラー アイコンに設定することができます。 ときに、<xref:System.Windows.Forms.ErrorProvider.DataSource%2A>プロパティが設定されて、<xref:System.Windows.Forms.ErrorProvider>コンポーネントは、データセットのエラー メッセージを表示できます。 主要なメソッド、<xref:System.Windows.Forms.ErrorProvider>コンポーネントは、<xref:System.Windows.Forms.ErrorProvider.SetError%2A>メソッド、エラー メッセージ文字列を指定して、エラー アイコンが表示されます。  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ErrorProvider>コンポーネントがユーザー補助クライアントの組み込みサポートを提供していません。 アプリケーション アクセスできるようにする場合、このコンポーネントを使用して、アクセス可能な追加のフィードバック メカニズムを提供する必要があります。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.ErrorProvider>  
 [方法: Windows フォーム ErrorProvider コンポーネントで DataSet 内にエラーを表示する](../../../../docs/framework/winforms/controls/view-errors-within-a-dataset-with-wf-errorprovider-component.md)  
 [方法: Windows フォーム ErrorProvider コンポーネントを使用してフォーム検証でエラー アイコンを表示する](../../../../docs/framework/winforms/controls/display-error-icons-for-form-validation-with-wf-errorprovider.md)
