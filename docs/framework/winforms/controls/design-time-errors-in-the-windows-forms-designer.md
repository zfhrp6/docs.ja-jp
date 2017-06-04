---
title: "Windows フォーム デザイナーでのデザイン時エラー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "DTELErrorList"
  - "WhyDTELPage"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "デザイン時エラー [Windows フォーム デザイナー]"
  - "エラー [Windows フォーム デザイナー]"
ms.assetid: ad408380-825a-46d8-9a4a-531b130b88ce
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Windows フォーム デザイナーでのデザイン時エラー
ここでは、Microsoft Visual Studio で Windows フォーム デザイナーの読み込みに失敗したときに表示される、デザイン時エラー一覧の意味と使用方法について説明します。  このエラー一覧の表示を、デザイナーのバグと解釈しないでください。この一覧は、コード内のエラーの修正を支援するために表示されます。  
  
 このエラー一覧の基本を理解し、エラーの詳細と推奨する解決方法の説明を表示することで、アプリケーションのデバッグを容易にすることができます。  
  
## デザイン時エラー一覧インターフェイス  
 Windows フォーム デザイナーが読み込みに失敗すると、デザイナーにエラー一覧が表示されます。  エラーは、カテゴリ別にグループ化されます。  たとえば、宣言されていない変数のインスタンスが 4 つあった場合、それらは、同じエラー カテゴリにグループ化されます。  各エラー カテゴリには、そのエラーの概要を示す短い説明が含まれます。  
  
 エラー カテゴリは、エラー カテゴリ見出しをクリックするか、展開\/縮小シェブロンをクリックすることで、展開または縮小できます。  エラー カテゴリを展開すると、次の追加ヘルプが表示されます。  
  
-   このエラーのインスタンス。  
  
-   このエラーのヘルプ。  
  
-   このエラーに関するフォーラム ポスト。  
  
### このエラーのインスタンス。  
 追加ヘルプには、現在のプロジェクトで発生したすべてのエラー インスタンスが一覧表示されます。  多くのエラーは、エラーの発生場所を示す次の形式の情報を含みます。*\[プロジェクト名\]* *\[フォーム名\]* 行 : *\[行番号\]* 列 : *\[列番号\]*.  **\[コードに移動\]** リンクをクリックすると、コード内のエラーの発生場所にジャンプします。  
  
 エラーに呼び出し履歴が関連付けられている場合は、**\[コール スタックの表示\]** リンクをクリックすると、エラーがさらに展開され、呼び出し履歴が表示されます。  履歴を調べることで、有用なデバッグ情報を得ることができます。  たとえば、エラーが発生する前に呼び出されていた関数を追跡できます。  呼び出し履歴は選択可能なので、コピーして保存することができます。  
  
> [!NOTE]
>  Visual Basic では、デザイン時エラー一覧に複数のエラーは表示されませんが、同じエラーの複数のインスタンスが表示される場合があります。  Visual C\+\+ では、エラーに \[コードに移動\] リンク\/行番号リンクは含まれません。  
  
### このエラーのヘルプ  
 エラーに関連付けられている MSDN ヘルプ トピックがある場合は、そのヘルプ トピックへのリンクが追加ヘルプに含まれます。  このリンクをクリックすると、関連付けられているヘルプ トピックが Visual Studio に表示されます。  
  
### このエラーに関するフォーラム ポスト  
 追加ヘルプは、エラーに関連する MSDN フォーラム ポストへのリンクを含みます。  フォーラムは、エラー メッセージの文字列に基づいて検索されます。  また、次のフォーラムを検索することもできます。  
  
-   [Windows Forms Designer Forum \(Windows フォーム デザイナー フォーラム\)](http://go.microsoft.com/fwlink/?LinkId=203524)  
  
-   [Windows Forms Forums \(Windows フォーム フォーラム\)](http://go.microsoft.com/fwlink/?LinkId=203523)  
  
### 無視と続行  
 エラー状態を無視して、デザイナーの読み込みを続行することを選択できます。  この操作を選択すると、予期しない動作が発生する場合があります。  たとえば、デザイン画面にコントロールが表示されない場合があります。  
  
## 参照  
 [Troubleshooting Design\-Time Development](../Topic/Troubleshooting%20Design-Time%20Development.md)   
 [コントロールとコンポーネントの作成時のトラブルシューティング](../../../../docs/framework/winforms/controls/troubleshooting-control-and-component-authoring.md)   
 [デザイン時の Windows フォーム コントロールの開発](../../../../docs/framework/winforms/controls/developing-windows-forms-controls-at-design-time.md)   
 [Windows Forms Designer Error Messages](http://msdn.microsoft.com/ja-jp/cf610bf4-5fe4-471c-bce7-6a05ece07bd2)