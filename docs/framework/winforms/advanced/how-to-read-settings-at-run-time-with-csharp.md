---
title: "方法 : 実行時に設定を C# で読み取る | Microsoft Docs"
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
  - "アプリケーション設定 [Windows フォーム], C#"
  - "アプリケーション設定 [Windows フォーム], 読み取り"
  - "アプリケーション設定 [Windows フォーム], 実行時に"
ms.assetid: dbe8bf09-5e1c-49da-9192-154033d7240b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 実行時に設定を C# で読み取る
アプリケーション スコープの設定とユーザー スコープの設定は、どちらも実行時に Properties オブジェクトを使用して読み取ることができます。  Properties オブジェクトは、プロジェクトのすべての既定の設定を、Properties.Settings.Default メンバーを介して公開します。  
  
### 実行時に設定を C\# で読み取るには  
  
-   Properties.Settings.Default メンバーを介して適切な設定にアクセスします。  BackColor プロパティに `myColor` という名前の設定を割り当てる方法を次の例に示します。  この例を実行する前に、`myColor` という名前の `System.Drawing.Color` 型の設定を含む設定ファイルを作成しておく必要があります。  設定ファイルを作成する方法の詳細については、「[方法 : 設計時に新しい設定を作成する](../../../../docs/framework/winforms/advanced/how-to-create-a-new-setting-at-design-time.md)」を参照してください。  
  
    ```  
    // C#  
    this.BackColor = Properties.Settings.Default.myColor;  
    ```  
  
## 参照  
 [アプリケーション設定とユーザー設定の使用](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [方法 : 実行時にユーザー設定を C\# で書き込む](../../../../docs/framework/winforms/advanced/how-to-write-user-settings-at-run-time-with-csharp.md)   
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)