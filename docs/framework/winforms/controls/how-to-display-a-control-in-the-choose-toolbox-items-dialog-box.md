---
title: "方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- global assembly cache [Windows Forms], Choose Toolbox Items dialog box
- AssemblyFoldersEx [Windows Forms], Choose Toolbox Items dialog box
- controls [Windows Forms], display in Choose Toolbox Items dialog box
- assembly folder registration [Windows Forms], Choose Toolbox Items dialog box
- Choose Toolbox Items dialog box [Windows Forms], display control
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1323ffbd59a14d19d1161e0718fad083bcc37a89
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-a-control-in-the-choose-toolbox-items-dialog-box"></a>方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する
を作成およびコントロールを配置することがそれらのコントロールに表示される、**ツールボックス アイテムの選択**を右クリックしたときに表示されるダイアログ ボックスで、**ツールボックス**選択**項目を選択して**です。 AssemblyFoldersEx 登録手順を使用してこのダイアログ ボックスに表示するコントロールを有効にすることができます。  
  
### <a name="to-display-your-control-in-the-choose-toolbox-items-dialog-box"></a>ツールボックス アイテムの選択 ダイアログ ボックスで、コントロールを表示するには  
  
-   コントロール アセンブリをグローバル アセンブリ キャッシュにインストールします。 詳細については、次を参照してください[する方法: グローバル アセンブリ キャッシュにアセンブリをインストール。](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
  
     - または -  
  
-   AssemblyFoldersEx 登録手順を使用して、コントロールとその関連付けられたデザイン時アセンブリを登録します。 AssemblyFoldersEx は、サード パーティ ベンダーがサポートされる framework の各バージョンのパスを格納する場所のレジストリの場所です。 デザイン時の解像度は、この参照アセンブリを検索するレジストリの場所で確認できます。 レジストリ スクリプトは、ツールボックスに表示するコントロールを指定できます。 詳細については、次を参照してください。[カスタム コントロールとデザイン時アセンブリ (Visual Studio 2013) の展開](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)です。  
  
## <a name="see-also"></a>参照  
 [[ツールボックス アイテムの選択] ダイアログ ボックス (Visual Studio)](http://msdn.microsoft.com/en-us/bd07835f-18a8-433e-bccc-7141f65263bb)  
 [カスタム コントロールとデザイン時アセンブリ (Visual Studio 2013) の展開](http://msdn.microsoft.com/en-us/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)  
 [デザイン時の Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)  
 [方法: グローバル アセンブリ キャッシュにアセンブリをインストールする](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)  
 [チュートリアル: ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)
