---
title: "方法 : C# のアプリケーションに複数の設定セットを追加する | Microsoft Docs"
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
  - "アプリケーション設定 [Windows フォーム], 複数セット"
ms.assetid: 45007ac6-cf07-4be7-bc38-3f0ef962faf9
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : C# のアプリケーションに複数の設定セットを追加する
アプリケーションの中に、複数の設定セットを用意する場合があります。  たとえば、特定のグループの設定だけが頻繁に変更されると想定されるアプリケーションを開発する場合は、それらの設定を 1 つのファイルに分離しておき、他の設定に影響を与えることなく、そのファイル全体を置換できるようにすると便利です。  Visual Studio では、複数の設定セットをプロジェクトに追加できます。  追加の設定セットには、Properties.Settings オブジェクトを介してアクセスできます。  
  
### アプリケーションに追加の設定セットを追加するには  
  
1.  **\[プロジェクト\]** メニューの **\[新しい項目の追加\]** をクリックします。  **\[新しい項目の追加\]** ダイアログ ボックスが表示されます。  
  
2.  **\[新しい項目の追加\]** ダイアログ ボックスで、**\[設定ファイル\]** をクリックし、ファイルの名前を入力します。次に、**\[追加\]** をクリックして、新しい設定ファイルをソリューションに追加します。  
  
3.  **ソリューション エクスプローラー**で、新しい設定ファイルを **\[プロパティ\]** フォルダーにドラッグします。  これで、新しい設定をコード内で使用できます。  
  
4.  他の設定ファイルと同じように、このファイルに設定を追加し、ファイルの設定を使用します。  このグループの設定は、Properties.Settings オブジェクトを介してアクセスできます。  
  
## 参照  
 [アプリケーション設定とユーザー設定の使用](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)   
 [アプリケーション設定の概要](../../../../docs/framework/winforms/advanced/application-settings-overview.md)