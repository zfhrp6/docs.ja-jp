---
title: Windows フォーム コントロール開発の基本概念
ms.date: 03/30/2017
helpviewer_keywords:
- custom controls [Windows Forms], derivation types
- programming concepts [Windows Forms], Windows Forms controls
- controls [Windows Forms], creating
ms.assetid: 6277bb81-90f7-4c5b-9f4b-b02bb42dd316
ms.openlocfilehash: b455912468376d2f5de0ac1f30b4fcab5bb93309
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541142"
---
# <a name="windows-forms-control-development-basics"></a>Windows フォーム コントロール開発の基本概念
Windows フォーム コントロールから直接または間接的に派生したクラスは、<xref:System.Windows.Forms.Control?displayProperty=nameWithType>です。 次の一覧には、Windows フォーム コントロールを開発するための一般的なシナリオについて説明します。  
  
-   複合コントロールを作成する既存の組み合わせを制御します。  
  
     複合コントロールには、コントロールとして再利用可能なユーザー インターフェイスがカプセル化します。 複合コントロールの例は、テキスト ボックスと [リセット] ボタンで構成されるコントロールです。 ビジュアル デザイナーでは、複合コントロールを作成するための豊富なサポートを提供します。 派生する複合コントロールを作成するには、<xref:System.Windows.Forms.UserControl?displayProperty=nameWithType>です。 基本クラス<xref:System.Windows.Forms.UserControl>キーボード ルーティングを提供する子コントロールおよび子コントロールがグループとして動作できるようにします。 詳細については、「[複合 Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)」を参照してください。  
  
-   それをカスタマイズする、またはその機能に追加する既存のコントロールを拡張します。  
  
     色を変更することはできません ボタンとボタンがクリックしてされた回数を追跡する追加のプロパティを持つ拡張コントロールの例に示します。 クラスを派生し、プロパティ、メソッド、およびイベントを追加、またはオーバーライドして、Windows フォーム コントロールをカスタマイズできます。  
  
-   結合や既存のコントロールを拡張しないコントロールを作成します。  
  
     このシナリオでは、基本クラスからコントロールを派生<xref:System.Windows.Forms.Control>です。 追加したり、プロパティ、メソッド、および基本クラスのイベントを上書きしたりします。 最初に、次を参照してください。[する方法: シンプルな Windows フォーム コントロールを開発](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)です。  
  
 Windows フォーム コントロールの基底クラス<xref:System.Windows.Forms.Control>、Windows ベースのクライアント側アプリケーションでのビジュアル表示に必要な組み込みを提供します。 <xref:System.Windows.Forms.Control> ウィンドウ ハンドル、メッセージのルーティングの処理し、マウスとキーボード イベントだけでなく他の多くのユーザー インターフェイスのイベントを提供します。 高度なレイアウトを提供し、視覚的に表示する固有のプロパティをなどが<xref:System.Windows.Forms.Control.ForeColor%2A>、 <xref:System.Windows.Forms.Control.BackColor%2A>、 <xref:System.Windows.Forms.Control.Height%2A>、 <xref:System.Windows.Forms.Control.Width%2A>、およびその他の多くのです。 さらに、セキュリティ、スレッド処理のサポート、および ActiveX コントロールとの相互運用性を提供します。 インフラストラクチャの大部分は基本クラスによって提供されるため、独自の Windows フォーム コントロールを比較的簡単に開発できます。  
  
## <a name="see-also"></a>関連項目  
 [方法: シンプルな Windows フォーム コントロールを開発する](../../../../docs/framework/winforms/controls/how-to-develop-a-simple-windows-forms-control.md)  
 [複合 Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-a-composite-windows-forms-control.md)  
 [方法: 進行状況を示す Windows フォーム コントロールを作成する](../../../../docs/framework/winforms/controls/how-to-create-a-windows-forms-control-that-shows-progress.md)  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
