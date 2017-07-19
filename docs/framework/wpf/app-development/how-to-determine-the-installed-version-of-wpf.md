---
title: "方法: インストールされている WPF のバージョンを確認する | Microsoft Docs"
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
  - "バージョン, 検索"
ms.assetid: 99971cef-e218-4f9f-a4c1-350332741860
caps.latest.revision: 3
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 3
---
# 方法: インストールされている WPF のバージョンを確認する
現在インストールされている [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のバージョン番号は、**レジストリ**にあります。  
  
 バージョン番号を確認するには、次の操作を実行します。  
  
1.  **\[スタート\]** メニューの **\[ファイル名を指定して実行\]** をクリックします。  
  
2.  \[名前 :\] に「**regedit.exe**」と入力します。  
  
3.  次のキーを開きます。  
  
 `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.0\Setup\Windows Presentation Foundation`  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のバージョン番号は、**Version** の値に格納されています。