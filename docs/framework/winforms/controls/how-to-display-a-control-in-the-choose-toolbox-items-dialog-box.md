---
title: "方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "グローバル アセンブリ キャッシュ、[ツールボックス アイテムの選択] ダイアログ ボックス"
  - "AssemblyFoldersEx、[ツールボックス アイテムの選択] ダイアログ ボックス"
  - "コントロール、[ツールボックス アイテムの選択] ダイアログ ボックスでの表示"
  - "アセンブリ フォルダー登録、[ツールボックス アイテムの選択] ダイアログ ボックス"
  - "[ツールボックス アイテムの選択] ダイアログ ボックス、コントロールの表示"
ms.assetid: 01ef6eba-d044-40f0-951d-78eff7ebd9a9
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 13
---
# 方法: [ツールボックス アイテムの選択] ダイアログ ボックスにコントロールを表示する
コントロールを作成して配布するときに、**\[ツールボックス アイテムの選択\]** ダイアログ ボックスにコントロールを表示できます。このダイアログ ボックスは、**ツールボックス**を右クリックし、**\[アイテムの選択\]** をクリックすると表示されます。  このダイアログ ボックスにコントロールを表示できるようにするには、AssemblyFoldersEx 登録プロシージャを使用します。  
  
### \[ツールボックス アイテムの選択\] ダイアログ ボックスにコントロールを表示するには  
  
-   コントロール アセンブリをグローバル アセンブリ キャッシュにインストールします。  詳細については、「[方法 : グローバル アセンブリ キャッシュにアセンブリをインストールする](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)」を参照してください。  
  
     または  
  
-   AssemblyFoldersEx 登録プロシージャを使用して、コントロールとそれに関連付けられているデザイン時アセンブリを登録します。  AssemblyFoldersEx は、サードパーティ ベンダーでサポートされているフレームワークの各バージョンのパスを格納するレジストリの位置です。  このレジストリの位置でデザイン時の解決を調べると、参照アセンブリを確認できます。  レジストリ スクリプトでツールボックスに表示するコントロールを指定できます。  詳細については、「[カスタム コントロールとデザイン時アセンブリの配置](http://msdn.microsoft.com/ja-jp/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)」を参照してください。  
  
## 参照  
 [Choose Toolbox Items Dialog Box \(Visual Studio\)](http://msdn.microsoft.com/ja-jp/bd07835f-18a8-433e-bccc-7141f65263bb)   
 [カスタム コントロールとデザイン時アセンブリの配置](http://msdn.microsoft.com/ja-jp/96158eb0-b691-4ae1-9e7b-3c65a1b798cb)   
 [デザイン時の Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [方法 : グローバル アセンブリ キャッシュにアセンブリをインストールする](../../../../docs/framework/app-domains/how-to-install-an-assembly-into-the-gac.md)   
 [チュートリアル : ツールボックスへのカスタム コンポーネントの自動設定](../../../../docs/framework/winforms/controls/walkthrough-automatically-populating-the-toolbox-with-custom-components.md)