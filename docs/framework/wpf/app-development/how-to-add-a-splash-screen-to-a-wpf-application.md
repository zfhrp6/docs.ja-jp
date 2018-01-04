---
title: "方法 : スプラッシュ スクリーンを WPF アプリケーションに追加する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1ed9669479a3854c843716a1aeb37f7701ea7d7b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>方法 : スプラッシュ スクリーンを WPF アプリケーションに追加する
このトピックは、[スタートアップ] ウィンドウを追加する方法を示しますまたは*スプラッシュ スクリーン*、Windows Presentation Foundation (WPF) アプリケーションにします。  
  
### <a name="to-add-an-existing-image-as-a-splash-screen"></a>スプラッシュ スクリーンとして既存のイメージを追加するには  
  
1.  スプラッシュ スクリーンを使用するイメージを作成または選択します。 Windows イメージング コンポーネント (WIC) ではサポートされているすべてのイメージ形式を使用することができます。 たとえば、BMP、GIF、JPEG、PNG、または TIFF の形式を使用することができます。  
  
2.  WPF アプリケーション プロジェクトにイメージ ファイルを追加します。 詳細については、次を参照してください。 [NIB: 方法: 既存の項目をプロジェクトに追加](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)です。  
  
3.  ソリューション エクスプ ローラーで、イメージを選択します。  
  
4.  [プロパティ] ウィンドウでのドロップダウン矢印をクリックして、**ビルド アクション**プロパティです。  
  
5.  選択**SplashScreen**ドロップダウン リストからです。  
  
    > [!NOTE]
    >  表示されない場合、 **SplashScreen**オプションを使用していることを確認してください[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)]SP1 またはそれ以降。  
  
6.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
     スプラッシュ スクリーンのイメージは、画面の中央に表示され、アプリケーションのメイン ウィンドウが表示されたら、フェードし。  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>スプラッシュ スクリーンをアプリケーションから削除するには  
  
1.  ソリューション エクスプ ローラーでは、スプラッシュ スクリーンのイメージを選択します。  
  
2.  [プロパティ] ウィンドウで、設定、**ビルド アクション**に**なし**です。  
  
### <a name="to-remove-the-splash-screen-from-an-application"></a>スプラッシュ スクリーンをアプリケーションから削除するには  
  
-   ソリューション エクスプ ローラーでは、スプラッシュ スクリーンのイメージを削除します。  
  
-   スプラッシュ スクリーンのイメージをプロジェクトから除外します。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.SplashScreen>  
 [NIB: 方法: 既存の項目をプロジェクトに追加します。](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)
