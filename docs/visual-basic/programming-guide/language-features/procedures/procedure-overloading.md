---
title: "Procedure Overloading (Visual Basic) | Microsoft Docs"
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
  - "signatures"
  - "Overloads keyword"
  - "hiding by signature"
  - "Visual Basic code, procedures"
  - "procedures, signatures for"
  - "procedures, overloading"
  - "procedures, multiple versions"
  - "parameters, lists"
  - "signatures, procedure"
  - "parameter lists"
  - "Visual Basic code, parameter lists"
  - "Shadows keyword"
  - "procedure overloading"
  - "procedures, parameter lists"
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# Procedure Overloading (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

プロシージャの*オーバーロード*とは、名前が同じでパラメーター リストが異なる、複数のバージョンのプロシージャを定義することです。  プロシージャをオーバーロードする目的は、互いに密接な関係にある複数のバージョンのプロシージャを、名前で区別せずに定義することにあります。  バージョンごとに異なるパラメーター リストを使用することによって、これが可能になります。  
  
## オーバーロードの規則  
 プロシージャをオーバーロードする場合は、次のような規則があります。  
  
-   **同じ名前**。  オーバーロードされた各バージョンは、同じプロシージャ名を使用する必要があります。  
  
-   **別のシグネチャ**。  オーバーロードされた各バージョンは、次のうちの少なくとも 1 つが他のすべてのバージョンと異なっている必要があります。  
  
    -   パラメーターの数  
  
    -   パラメーターの順序  
  
    -   パラメーターのデータ型  
  
    -   型パラメーターの数 \(ジェネリック プロシージャの場合\)  
  
    -   戻り値の型 \(変換演算子のみ\)  
  
     プロシージャ名と共に、上記の項目はまとめて、プロシージャの*シグネチャ*と呼ばれます。  オーバーロードされたプロシージャを呼び出す場合、コンパイラはシグネチャを使って、呼び出しが定義と一致しているかどうかを確認します。  
  
-   **シグネチャに含まれない項目**。  プロシージャをオーバーロードするには、シグネチャを変更する必要があります。  以下の要素を変更するだけでは、プロシージャをオーバーロードすることはできません。  
  
    -   `Public`、`Shared`、`Static` などのプロシージャ修飾子キーワード  
  
    -   パラメーターまたは型パラメーターの名前  
  
    -   型パラメーターの制約 \(ジェネリック プロシージャの場合\)  
  
    -   `ByRef` や `Optional` などのパラメーター修飾子キーワード  
  
    -   値を返すかどうか  
  
    -   戻り値のデータ型 \(変換演算子以外\)  
  
     上記のリスト項目は、シグネチャの一部ではありません。  これらを使って複数のオーバーロードされたバージョンを区別することはできませんが、シグネチャによって適切に差別化されたオーバーロードされたバージョンのそれぞれで、これらの要素が異なっていてもかまいません。  
  
-   **遅延バインディングの引数**。  遅延バインディング オブジェクト変数をオーバーロードされたバージョンに渡す場合は、適切なパラメーターを <xref:System.Object> として宣言する必要があります。  
  
## プロシージャの複数のバージョン  
 たとえば、顧客の残高に対してトランザクションをポストする `Sub` プロシージャを記述する場合に、名前と口座番号のどちらでも顧客を参照できるようにするとします。  これを行うには、次のように、2 つの異なる `Sub` プロシージャを定義する方法があります。  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### オーバーロードされたバージョン  
 この他に、1 つのプロシージャ名をオーバーロードする方法もあります。  [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md) キーワードを使って、次のように、各パラメーター リストごとにプロシージャのバージョンを定義します。  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### 追加のオーバーロード  
 トランザクションの額を `Decimal` と `Single` のどちらで受け取ることもできるようにするには、`post` をさらにオーバーロードします。  上の例のオーバーロードされた各バージョンをさらにオーバーロードすると、名前が同じでシグネチャがそれぞれ異なる `Sub` プロシージャが 4 つできることになります。  
  
## オーバーロードの利点  
 プロシージャのオーバーロードの利点は、呼び出しの柔軟性にあります。  上の例で宣言した `post` プロシージャを使用する場合、呼び出し元のコードでは、顧客の ID を `String` として取得することも `Integer` として取得することもできます。いずれの場合も、呼び出すプロシージャは同じです。  次に例を示します。  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## 参照  
 [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md)   
 [How to: Define Multiple Versions of a Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-multiple-versions-of-a-procedure.md)   
 [How to: Call an Overloaded Procedure](../../../../visual-basic/programming-guide/language-features/procedures/how-to-call-an-overloaded-procedure.md)   
 [How to: Overload a Procedure that Takes Optional Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-optional-parameters.md)   
 [How to: Overload a Procedure that Takes an Indefinite Number of Parameters](../../../../visual-basic/programming-guide/language-features/procedures/how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)   
 [Considerations in Overloading Procedures](../../../../visual-basic/programming-guide/language-features/procedures/considerations-in-overloading-procedures.md)   
 [Overload Resolution](../../../../visual-basic/programming-guide/language-features/procedures/overload-resolution.md)   
 [Overloads](../../../../visual-basic/language-reference/modifiers/overloads.md)   
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)