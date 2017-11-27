---
title: "方法 : 設計時に新しい設定を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- application settings [Windows Forms], design time
- application settings [Windows Forms], creating
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3e8a05b6f37f7686f18a6200e009aabe7eed5537
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-new-setting-at-design-time"></a>方法 : 設計時に新しい設定を作成する
デザイン時に、新しい設定を作成するには、設定デザイナーを使用します。 設定デザイナーは、グリッド スタイル インターフェイスを使用すると、新しい設定を作成し、それらの設定のプロパティを指定します。 名前、値、型、および、新しい設定のスコープを指定する必要があります。 設定が作成されるは、コード内でアクセスします。  
  
### <a name="to-create-a-new-setting-at-design-time-in-c"></a>C# でのデザイン時に新しい設定を作成するには  
  
1.  **ソリューション エクスプ ローラー**、展開、**プロパティ**プロジェクトのノードです。  
  
2.  新しい設定を追加する .settings ファイルをダブルクリックします。 このファイルの既定の名前は、Settings.settings です。  
  
3.  設定デザイナーでは、名前、値、型、およびスコープを設定を設定します。 各行は、1 つの設定を表します。  
  
### <a name="to-create-a-new-setting-at-design-time-in-visual-basic"></a>Visual Basic でのデザイン時に新しい設定を作成するには  
  
1.  **ソリューション エクスプ ローラー**をプロジェクト ノードを右クリックして**プロパティ**です。  
  
2.  **プロパティ**] ページで、[、**設定**タブです。  
  
3.  設定デザイナーでは、名前、値、型、およびスコープを設定を設定します。 各行は、1 つの設定を表します。  
  
## <a name="see-also"></a>関連項目  
 [アプリケーション設定とユーザー設定の使用](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)  
 [方法: 設計時に既存の設定の値を変更する](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)
