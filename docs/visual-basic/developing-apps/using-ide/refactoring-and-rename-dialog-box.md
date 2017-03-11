---
title: "リファクタリングと [名前の変更] ダイアログ ボックス (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.RenameSymbol"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "シンボル、名前の変更"
  - "名前、シンボルの変更"
  - "[名前の変更] ダイアログ ボックス"
ms.assetid: 001d2d81-9bb6-4e8e-ae3a-20c0daaa3959
redirect_url: https://msdn.microsoft.com/library/ckfya594(v=vs.140).aspx
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# リファクタリングと [名前の変更] ダイアログ ボックス (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic の組み込み **\[名前の変更\]** ダイアログ ボックスを使用すると、フィールド、ローカル変数、メソッド、名前空間、プロパティ、型などのシンボルを表す、コードに含まれている識別子の名前を変更できます。  **\[名前の変更\]** ダイアログ ボックスを開くには、要素の宣言を右クリックします。  
  
 **\[新しい名前\]**  
 コード要素の新しい名前を指定します。  
  
 **\[場所\]**  
 名前の変更操作を実行するときに検索する名前空間を指定します。  
  
## 名前変更の操作  
 **\[名前の変更\]** ダイアログ ボックスで実行される名前変更の操作は、名前を変更する要素の型によって多少異なります。  
  
|要素の型|名前変更の操作|  
|----------|-------------|  
|Class|当該クラスのすべての宣言とすべての使用箇所が、新しい名前に変更されます。  部分クラスについては、名前変更の操作はすべての部分に反映されます。|  
|Field|当該フィールドの宣言と使用箇所が、新しい名前に変更されます。|  
|ローカル変数|当該変数の宣言と使用箇所が、新しい名前に変更されます。|  
|メソッド|当該メソッドの名前と、当該メソッドへのすべての参照が、新しい名前に変更されます。|  
|名前空間|宣言、すべての `Imports` ステートメント、およびすべての完全修飾名において、当該名前空間の名前が新しい名前に変更されます。|  
|プロパティ|当該プロパティの宣言と使用箇所が、新しい名前に変更されます。|  
  
## リファクタリング  
 Visual Basic と Developer Express Inc. との提携により、  綿密なリファクタリングを行うことができます。  このツールをダウンロードする方法の詳細については、MSDN の Visual Basic デベロッパー センターで [Refactor\!](http://go.microsoft.com/fwlink/?LinkId=155788) を参照してください。  Refactor\! は   15 個以上のリファクタリング機能をサポートしています。  その中には、パラメーター順序の再変更、メソッドの抽出、フィールドのカプセル化、およびオーバーロードの作成が含まれています。  
  
## 参照  
 [Using the Visual Basic Development Environment](../../../visual-basic/developing-apps/using-ide/using-the-visual-basic-development-environment.md)