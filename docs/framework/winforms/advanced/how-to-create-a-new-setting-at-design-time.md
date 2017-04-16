---
title: "方法 : 設計時に新しい設定を作成する | Microsoft Docs"
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
  - "アプリケーション設定 [Windows フォーム], 作成"
  - "アプリケーション設定 [Windows フォーム], デザイン時"
ms.assetid: c5d60a66-6507-462f-a81f-e3bc0a804e16
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 設計時に新しい設定を作成する
設定デザイナーを使用して、設計時に新しい設定を作成できます。  設定デザイナーは、新しい設定を作成して各設定のプロパティを指定できるグリッド スタイルのインターフェイスです。  新しい設定には、名前、値、種類、およびスコープを指定する必要があります。  作成した設定は、コード内でアクセスできます。  
  
### 設計時に C\# で新しい設定を作成するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクトの **\[プロパティ\]** ノードを展開します。  
  
2.  新しい設定を追加する .settings ファイルをダブルクリックします。  このファイルの既定の名前は Settings.settings です。  
  
3.  設定デザイナーで、設定の名前、値、種類、およびスコープを設定します。  各行が 1 つの設定を表します。  
  
### 設計時に Visual Basic で新しい設定を作成するには  
  
1.  **ソリューション エクスプローラー** で、プロジェクト ノードを右クリックし、**\[プロパティ\]** をクリックします。  
  
2.  **\[プロパティ\]** ページの **\[設定\]** タブをクリックします。  
  
3.  設定デザイナーで、設定の名前、値、種類、およびスコープを設定します。  各行が 1 つの設定を表します。  
  
## 参照  
 [アプリケーション設定とユーザー設定の使用](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)   
 [方法 : 設計時に既存の設定の値を変更する](../../../../docs/framework/winforms/advanced/how-to-change-the-value-of-an-existing-setting-at-design-time.md)