---
title: "Differences Between Shadowing and Overriding (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "shadowing, vs. overriding"
  - "overriding, vs. shadowing"
ms.assetid: 2d014a0b-7630-407d-8f4e-24bd87987923
caps.latest.revision: 24
caps.handback.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Differences Between Shadowing and Overriding (Visual Basic)
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

基本クラスを継承するクラスを定義する際に、基本クラスの要素のいくつかを派生クラスで再定義する場合があります。  シャドウとオーバーライドは、どちらもこの目的で使用できます。  
  
## 比較  
 シャドウとオーバーライドはどちらも、派生クラスが基本クラスから継承するときに使用され、宣言された要素を他の要素で再定義します。  しかし、シャドウとオーバーライドの間には大きな違いがあります。  
  
 シャドウとオーバーライドの比較を次の表に示します。  
  
||||  
|-|-|-|  
|比較のポイント|Shadowing|オーバーライド|  
|目的|派生クラスで既に定義されているメンバーを追加するような基本クラスの変更を防ぐ|呼び出しシーケンスが同じで実装が異なるプロシージャまたはプロパティを定義することにより、ポリモーフィズムを実現する <sup>1</sup>|  
|再定義される要素|任意の宣言された要素型|プロシージャ \(`Function`、`Sub`、`Operator`\) またはプロパティのみ|  
|再定義する要素|任意の宣言された要素型|呼び出しシーケンスが同じプロシージャまたはプロパティのみ <sup>1</sup>|  
|再定義する要素のアクセス レベル|任意のアクセス レベル|オーバーライドされた要素のアクセス レベルは変更できない|  
|再定義する要素の読み取りと書き込みの許可|任意の組み合わせ|オーバーライドされたプロパティの読み取りと書き込みの許可は変更できない|  
|再定義の制御|基本クラスの要素にシャドウを強制または禁止することはできない|基本クラスの要素に `MustOverride`、`NotOverridable` または `Overridable` を指定できる|  
|キーワードの使用法|派生クラスでは `Shadows` を推奨。`Shadows` と `Overrides` のどちらも指定されない場合は、`Shadows` と見なされる <sup>2</sup>|基本クラスでは `Overridable` または `MustOverride` が必要。派生クラスでは `Overrides` が必要|  
|派生クラスから派生するクラスでの、再定義する要素の継承|シャドウする要素は以降の派生クラスでも継承され、シャドウされる要素は引き続き隠される <sup>3</sup>|オーバーライドする要素は以降の派生クラスでも継承され、オーバーライドされる要素は引き続きオーバーライドされる|  
  
 <sup>1</sup> *呼び出しシーケンス*は、要素型 \(`Function`、`Sub`、`Operator`、または `Property`\)、名前、パラメーター リスト、および戻り値の型で構成されます。  プロシージャをプロパティでオーバーライドしたり、プロパティをプロシージャでオーバーライドしたりはできません。  ある種類のプロシージャ \(`Function`、`Sub`、または `Operator`\) を他の種類のプロシージャでオーバーライドすることはできません。  
  
 <sup>2</sup> `Shadows` と `Overrides` のどちらも指定していない場合、どちらの再定義を使用するのかを確認するよう促すための警告メッセージがコンパイラから出力されます。  警告を無視すると、シャドウが使用されます。  
  
 <sup>3</sup> 派生クラスからさらに派生するクラスで、シャドウする側の要素にアクセスできない場合、シャドウは継承されません。  たとえば、シャドウする側の要素を `Private` として宣言した場合、派生クラスから派生するクラスは、その要素の代わりに元の要素を継承します。  
  
## ガイドライン  
 次のような場合は、通常、オーバーライドを使用します。  
  
-   ポリモーフィックな派生クラスを定義している場合。  
  
-   安全のために、コンパイラで同一の要素型と呼び出しシーケンスを適用させる場合。  
  
 次のような場合は、通常、シャドウを使用します。  
  
-   基本クラスが変更される可能性があり、使用している名前と同じ名前で要素を定義する可能性がある場合。  
  
-   要素型や呼び出しシーケンスを自由に変更できるようにする場合。  
  
## 参照  
 [References to Declared Elements](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)   
 [Shadowing in Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)   
 [How to: Hide a Variable with the Same Name as Your Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)   
 [How to: Hide an Inherited Variable](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)   
 [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)   
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)   
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)