---
title: "エンコード方式および Windows フォームのグローバリゼーション | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "DateTimePicker コントロール [Windows フォーム], Unicode サポートのない"
  - "グローバリゼーション [Windows フォーム], 文字セット"
  - "ImageList コンポーネント [Windows フォーム], Unicode サポートのない"
  - "国際対応のアプリケーション [Windows フォーム], 文字表示"
  - "各種言語の文字"
  - "ListView コントロール [Windows フォーム], Unicode サポートのない"
  - "ローカリゼーション [Windows フォーム], 文字セット"
  - "MonthCalendar コントロール [Windows フォーム], Unicode サポートのない"
  - "ProgressBar コントロール [Windows フォーム], Unicode 対応フォーム"
  - "StatusBar コントロール [Windows フォーム], Unicode サポートのない"
  - "TabControl コントロール [Windows フォーム], Unicode サポートのない"
  - "ToolBar コントロール [Windows フォーム], Unicode サポートのない"
  - "TrackBar コントロール [Windows フォーム], Unicode サポートのない"
  - "TreeView コントロール [Windows フォーム], Unicode サポートのない"
  - "Unicode [Windows フォーム]"
  - "Windows フォーム, エンコーディング"
ms.assetid: 22e8965d-a712-42b3-8167-3ee346bd70f9
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# エンコード方式および Windows フォームのグローバリゼーション
Windows フォーム アプリケーションは、Unicode に完全対応しているため、プラットフォーム、プログラム、または言語に関係なく、文字がそれぞれ一意の数字で表されます。  Unicode の詳細については、[Unicode コンソーシアムの Web サイト](http://www.unicode.org)を参照してください。  
  
## Unicode の利点  
 Unicode 対応フォームの利点として、ヒンディー語などの Unicode 専用のスクリプトを操作できる点も含まれます。  さらに、1 つのフォームで複数の言語を使用できます。  Unicode では、すべての文字が 2 バイト長なので、2 バイト文字を表すために特別な作業は必要ありません。  また、すべてのプラットフォームで動作する 1 つのコードのセットを作成することもできます。  これは、Windows NT や [!INCLUDE[win98](../../../../includes/win98-md.md)] など、プラットフォームが異なると別のコードを作成する必要がある、以前のバージョンの [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] から変更されています。  
  
 ただし、[!INCLUDE[win98](../../../../includes/win98-md.md)] および Windows Millennium Edition では、特定のコントロールが Unicode をサポートしません。  これらのコントロールはすべてコモン コントロールから継承されていて、Windows コード ページで [!INCLUDE[vcpransi](../../../../includes/vcpransi-md.md)] としてデータを処理します。  これらのコントロールは、<xref:System.Windows.Forms.TabControl>、<xref:System.Windows.Forms.ListView>、<xref:System.Windows.Forms.TreeView>、<xref:System.Windows.Forms.DateTimePicker>、<xref:System.Windows.Forms.MonthCalendar>、<xref:System.Windows.Forms.TrackBar>、<xref:System.Windows.Forms.ProgressBar>、<xref:System.Windows.Forms.ImageList>、<xref:System.Windows.Forms.ToolBar>、および <xref:System.Windows.Forms.StatusBar> です。  その結果、前述のプラットフォーム上のこれらのコントロールで Unicode データを表示することはできません。  たとえば、日本語の文字を英語の [!INCLUDE[win98](../../../../includes/win98-md.md)] オペレーティング システムで表示することはできません。  
  
 <xref:System.Windows.Forms.ToolBar> コントロールと <xref:System.Windows.Forms.StatusBar> コントロールの Unicode 対応の代替手段として、これらの古いコントロールを置換する <xref:System.Windows.Forms.ToolStrip> コントロールと <xref:System.Windows.Forms.StatusStrip> コントロールを使用します。  アプリケーションの視覚要素の間で同様のルック アンド フィールを維持するには、メニューの表示に <xref:System.Windows.Forms.MainMenu> の代わりに <xref:System.Windows.Forms.MenuStrip> コントロールを使用します。  <xref:System.Windows.Forms.ToolStrip> と <xref:System.Windows.Forms.StatusStrip> のように、<xref:System.Windows.Forms.MenuStrip> も Unicode 文字を処理して表示することができます。  
  
## 参照  
 [Windows フォームのグローバル化](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)