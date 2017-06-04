---
title: "方法 : スプラッシュ スクリーンを WPF アプリケーションに追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スプラッシュ スクリーン [WPF]"
  - "SplashScreen クラス [WPF]"
  - "スタートアップ ウィンドウ [WPF]"
  - "WPF, スプラッシュ スクリーン"
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
caps.latest.revision: 14
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 14
---
# 方法 : スプラッシュ スクリーンを WPF アプリケーションに追加する
このトピックでは、スタートアップ ウィンドウ、つまり*スプラッシュ スクリーン*を Windows Presentation Foundation \(WPF\) アプリケーションに追加する方法を示します。  
  
### 既存のイメージをスプラッシュ スクリーンとして追加するには  
  
1.  スプラッシュ スクリーンに使用するイメージを作成または検索します。  Windows イメージング コンポーネント \(WIC\) によってサポートされているイメージ形式はすべて使用できます。  たとえば、BMP、GIF、JPEG、PNG、TIFF 形式などが使用できます。  
  
2.  イメージ ファイルを WPF アプリケーション プロジェクトに追加します。  詳細については、「[NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/ja-jp/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)」を参照してください。  
  
3.  ソリューション エクスプローラーでイメージを選択します。  
  
4.  \[プロパティ\] ウィンドウで、**\[ビルド アクション\]** プロパティのドロップダウン矢印をクリックします。  
  
5.  ドロップダウン リストの **\[SplashScreen\]** をクリックします。  
  
    > [!NOTE]
    >  **\[SplashScreen\]** オプションが表示されない場合は、[!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)] SP1 以降を使用しているかどうかを確認してください。  
  
6.  F5 キーを押してアプリケーションをビルドし、実行します。  
  
     画面の中央にスプラッシュ スクリーンのイメージが表示されます。このイメージは、メインのアプリケーション ウィンドウが表示されると、フェード アウトします。  
  
### アプリケーションからスプラッシュ スクリーンを削除するには  
  
1.  ソリューション エクスプローラーで、スプラッシュ スクリーンのイメージを選択します。  
  
2.  \[プロパティ\] ウィンドウで、**\[ビルド アクション\]** を **\[なし\]** に設定します。  
  
### アプリケーションからスプラッシュ スクリーンを削除するには  
  
-   ソリューション エクスプローラーで、スプラッシュ スクリーンのイメージを削除します。  
  
-   スプラッシュ スクリーンのイメージをプロジェクトから除外します。  
  
## 参照  
 <xref:System.Windows.SplashScreen>   
 [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/ja-jp/15f4cfb7-78ab-457f-9f14-099a25a6a2d3)