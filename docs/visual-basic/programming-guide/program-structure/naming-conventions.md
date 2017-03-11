---
title: "Visual Basic Naming Conventions | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "names, Visual Basic rules"
  - "naming conventions"
  - "naming conventions, Visual Basic"
  - "Visual Basic code, naming conventions"
  - "conventions, Visual Basic coding"
  - "names, naming conventions"
  - "naming conventions, classes"
ms.assetid: 164949a4-2a7c-4736-9d82-9c3078e2e56c
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# Visual Basic Naming Conventions
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic アプリケーションの要素に名前を付ける場合は、最初の文字を英字、漢字、ひらがな、カタカナ、アンダースコア \(\_\) のいずれかにする必要があります。  ただし、アンダースコアで始まる名前は [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md) \(CLS\) に準拠しないので注意してください。  
  
 名前付けには以下の推奨事項が適用されます。  
  
-   `FindLastRecord` や `RedrawMyForm` のように、名前の各単語は大文字で開始します。  
  
-   `InitNameArray` や `CloseDialog` のように、関数名とメソッド名は動詞で開始します。  
  
-   `EmployeeName` や `CarAccessory` のように、クラス、構造体、モジュール、およびプロパティの名前は名詞で開始します。  
  
-   インターフェイス名は "I" で開始し、その後には `IComponent` のように名詞または名詞句を続けるか、または `IPersistable` のようにインターフェイスの動作を説明する形容詞を続けます。  アンダースコアは使用しないでください。また、省略形を使用すると混乱を招く可能性があるため、使用しないようにしてください。  
  
-   イベント ハンドラー名はイベントの種類を説明する名詞で開始し、その後にサフィックス "`EventHandler`" を付け、"`MouseEventHandler`" のように記述します。  
  
-   イベント引数クラスの名前には、サフィックス "`EventArgs`" を含めます。  
  
-   イベントに前後の概念がある場合は、"`ControlAdd`" や "`ControlAdded`" のように現在形または過去形を使用します。  
  
-   長い用語や頻繁に使用する用語は、省略形を使って名前を適切な長さにします。たとえば、"Hypertext Markup Language" の代わりに "HTML" を使用します。  通常、32 文字より長い変数名は、解像度の低いディスプレイでは読みにくくなります。  省略形は、必ずアプリケーション全体で統一してください。  プロジェクト内で "HTML" と "Hypertext Markup Language" の両方を不規則に使用すると混乱が生じます。  
  
-   外部スコープにある名前と同じ名前を内部スコープで使用することは避けてください。  不正な変数にアクセスされるとエラーが発生します。  同じ名前の変数とキーワードの間で競合が発生した場合は、適切なタイプ ライブラリを先頭に付けてキーワードを識別する必要があります。  たとえば `Date` という変数がある場合は、<xref:System.DateTime.Date%2A?displayProperty=fullName> の呼び出しによってのみ、組み込み関数 `Date` を使用できます。  
  
## 参照  
 [Keywords as Element Names in Code](../../../visual-basic/programming-guide/program-structure/keywords-as-element-names-in-code.md)   
 [Me, My, MyBase, and MyClass](../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)   
 [Declared Element Names](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)   
 [プログラム構造とコード規則](../../../visual-basic/programming-guide/program-structure/program-structure-and-code-conventions.md)   
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)