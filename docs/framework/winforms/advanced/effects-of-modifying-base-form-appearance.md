---
title: "基本フォームの外観を変更した場合の影響 | Microsoft Docs"
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
  - "基本フォーム"
  - "継承, フォーム"
  - "継承フォーム, 変更 (基本フォームに対する)"
  - "親フォーム"
  - "Windows フォーム, 基本フォームの外観"
ms.assetid: 1c3f2b29-a05c-4c6f-aa1a-4e66b94f343a
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 基本フォームの外観を変更した場合の影響
アプリケーションの開発時には、同じプロジェクト \(または他のプロジェクト\) 内の他のフォームの継承元となる、基本フォームの外観の変更が必要になることがよくあります。  
  
 デザイン時にプロパティ設定の変更やコントロールの追加または削除によって基本フォームの外観を変更すると、基本フォームを含むプロジェクトを作成するときに、その変更が継承先のフォームに反映されます。  基本フォームに対する変更を保存するだけでは、継承先のフォームに反映されません。  プロジェクトを作成するには、**\[ビルド\]** メニューの **\[ビルド\]** をクリックします。  
  
> [!NOTE]
>  実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。  設定を変更するには、**\[ツール\]** メニューの **\[設定のインポートとエクスポート\]** をクリックします。  詳細については、「[Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/ja-jp/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。  
  
 実行時に基本フォームに変更を加えても、既にインスタンス化された継承先のフォームには反映されません。  
  
## 参照  
 [base](../Topic/base%20\(C%23%20Reference\).md)   
 [方法 : Windows フォームを継承する](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)   
 [Windows フォームのビジュアルの継承](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)