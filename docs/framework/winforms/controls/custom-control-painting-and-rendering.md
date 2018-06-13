---
title: コントロールのカスタム描画およびレンダリング
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], rendering
- custom controls [Windows Forms], painting
- user controls [Windows Forms], painting
ms.assetid: a09dbf76-0966-4cbf-a66a-2083ba98e068
ms.openlocfilehash: 18a05a739f42d41a650e66723f44aae69c1707c7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33526052"
---
# <a name="custom-control-painting-and-rendering"></a>コントロールのカスタム描画およびレンダリング
コントロールのカスタム描画は、.NET Framework で簡単に作成する多くの複雑なタスクのいずれかです。 カスタム コントロールを作成するときに、コントロールの外観に関する多くのオプションがあります。 継承されるコントロールを作成している場合、 `Control`、グラフィカル表示を表示するために、コントロールを可能にするコードを指定する必要があります。 継承することで、ユーザー コントロールを作成するかどうかは、 `UserControl`、継承、または Windows フォーム コントロールのいずれかでは、標準のグラフィカル表示をオーバーライドして、独自のグラフィックス コードを提供します。 内在コントロールのカスタムの表示を提供するかどうか、`UserControl`オーサリングするは、これは、オプションが制限されますが、コントロールとアプリケーションのグラフィカル表現の広範な許可を許可します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [Windows フォーム コントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-a-windows-forms-control.md)  
 コントロールを表示するロジックをプログラミングする方法を示します。  
  
 [ユーザー描画コントロール](../../../../docs/framework/winforms/controls/user-drawn-controls.md)  
 コントロールの表示コードをオーバーライドしたりする書き込みに必要な手順の概要を示します。  
  
 [内在コントロール](../../../../docs/framework/winforms/controls/constituent-controls.md)  
 ユーザー コントロールおよびフォームに内在コントロールのカスタム表示コードを実装する方法について説明します。  
  
 [方法: 実行時にコントロールを非表示にする](../../../../docs/framework/winforms/controls/how-to-make-your-control-invisible-at-run-time.md)  
 使用する方法を示します、<xref:System.Windows.Forms.Control.Visible%2A>プロパティ コントロールの表示し、非表示にします。  
  
 [方法: コントロールに透明な背景を指定する](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)  
 使用する方法を示します、<xref:System.Windows.Forms.Control.SetStyle%2A>メソッドを非透過、透明で、または部分的に透明な背景色を作成します。  
  
 [visual スタイルが使用されているコントロールのレンダリング](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)  
 それらをサポートするオペレーティング システムで visual スタイルを使用してコントロールをレンダリングする方法を示します。  
  
## <a name="reference"></a>参照  
 <xref:System.Windows.Forms.Control>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.UserControl>  
 このクラスについて説明し、すべてのメンバーへのリンクの一覧を示します。  
  
 <xref:System.Windows.Forms.Control.OnPaint%2A>  
 このメソッドをについて説明します。  
  
## <a name="related-sections"></a>関連項目  
 [方法: 描画する Graphics オブジェクトを作成する](../../../../docs/framework/winforms/advanced/how-to-create-graphics-objects-for-drawing.md)  
 紹介[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]詳細については、Visual Studio によりとパースペクティブのリンクからグラフィックス機能します。  
  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)  
 作成できるカスタム コントロールの種類について説明します。
