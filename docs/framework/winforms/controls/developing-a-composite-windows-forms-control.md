---
title: "複合 Windows フォーム コントロールの開発"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- custom controls [Windows Forms], composite controls
- composite controls [Windows Forms]
- composite controls [Windows Forms], Windows Forms
- controls [Windows Forms], composite
ms.assetid: d086f2a3-baa3-4e09-b40c-a5bb3cfc51a6
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06ad98fef8c51cb995644c3b29236a9b0f8cfe29
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="developing-a-composite-windows-forms-control"></a>複合 Windows フォーム コントロールの開発
異なる複数の Windows フォーム コントロールを組み合わせることによって、複合 Windows フォーム コントロールを開発できます。 派生した複合コントロール<xref:System.Web.UI.UserControl>ユーザー コントロールと呼ばれます。 基底クラス <xref:System.Windows.Forms.UserControl> は、子コントロールに対してキーボード ルーティングを提供し、子コントロールがフォーカスを受け取れるようにします。 ユーザー コントロールの例は、次を参照してください。、<xref:System.Windows.Forms.UserControl>サンプルは、[する方法: Windows フォーム コントロールに属性を適用](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)です。  
  
 [!INCLUDE[vsprvsext](../../../../includes/vsprvsext-md.md)] の Windows フォーム デザイナーには、ユーザー コントロールを作成するための豊富なデザイン時サポートが用意されています。  
  
-   [方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する](http://msdn.microsoft.com/library/9yxtkx75\(v=vs.110\))  
  
-   [チュートリアル: DesignerSerializationVisibilityAttribute を使用した、標準データ型のコレクションのシリアル化](http://msdn.microsoft.com/library/ms171731\(v=vs.110\))  
  
-   [チュートリアル: Visual C# による Windows フォーム コントロールからの継承](http://msdn.microsoft.com/library/09476da0-8d4c-4a4c-b969-649519dfb438)  
  
-   [方法: コントロールにツールボックス ビットマップを指定する](http://msdn.microsoft.com/library/4wk1wc0a\(v=vs.110\))  
  
-   [方法: 既存の Windows フォーム コントロールから継承する](http://msdn.microsoft.com/library/7h62478z\(v=vs.110\))  
  
-   [チュートリアル: カスタム Windows フォーム コントロールのデザイン時のデバッグ](http://msdn.microsoft.com/library/5ytx0z24\(v=vs.110\))  
  
-   [方法: コントロール クラスを継承する](http://msdn.microsoft.com/library/skcysbt2\(v=vs.110\))  
  
-   [方法: UserControl の実行時の動作をテストする](http://msdn.microsoft.com/library/ms171738\(v=vs.110\))  
  
-   [方法: デザイン時にフォームの端に合わせてコントロールを配置する](http://msdn.microsoft.com/library/1fxyb15b\(v=vs.110\))  
  
-   [方法: UserControl クラスを継承する](http://msdn.microsoft.com/library/00ctb4z0\(v=vs.110\))  
  
-   [方法: Windows フォームのコントロールを作成する](http://msdn.microsoft.com/library/bs3yhkh7\(v=vs.110\))  
  
-   [方法: 複合コントロールを作成する](http://msdn.microsoft.com/library/3sf86w5h\(v=vs.110\))  
  
-   [チュートリアル: Visual Basic による複合コントロールの作成](http://msdn.microsoft.com/library/c316f119\(v=vs.110\))  
  
-   [チュートリアル: Visual C# による複合コントロールの作成](http://msdn.microsoft.com/library/f88481a8-c746-4a36-9479-374ce5f2e91f)  
  
-   [チュートリアル: Visual Basic による Windows フォーム コントロールからの継承](http://msdn.microsoft.com/library/w2a8y03d\(v=vs.110\))  
  
-   [方法: デザイン時機能を活用した Windows フォーム コントロールを作成する](http://msdn.microsoft.com/library/307hck25\(v=vs.110\))  
  
-   [方法: デザイン時機能を活用した Windows フォーム コントロールを作成する](http://msdn.microsoft.com/library/307hck25\(v=vs.120\))  
  
## <a name="see-also"></a>参照  
 [方法: Windows フォーム コントロールに属性を適用する](../../../../docs/framework/winforms/controls/how-to-apply-attributes-in-windows-forms-controls.md)  
 [.NET Framework を使用したカスタム Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [さまざまなカスタム コントロール](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)
