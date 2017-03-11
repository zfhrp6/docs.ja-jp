---
title: "方法: ジェネリック クラスを使用する (Visual Basic) | Microsoft Docs"
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
  - "型パラメーター、定義"
  - "データ型引数、定義"
  - "引数 [Visual Basic]、データ型"
  - "Of キーワード、使用"
  - "ジェネリック パラメーター"
  - "データ型パラメーター"
  - "ジェネリック [Visual Basic], ジェネリックの概要"
  - "データ型 [Visual Basic]、パラメーターとしての"
  - "データ型 [Visual Basic]、引数としての"
  - "パラメーター、型"
  - "型 [Visual Basic]、ジェネリック"
  - "パラメーター、ジェネリック"
  - "ジェネリック [Visual Basic], ジェネリック型の作成"
  - "データ型引数"
  - "パラメーター、データ型"
  - "データ型パラメーター、定義"
  - "型引数、定義"
  - "引数 [Visual Basic]、型"
ms.assetid: 242dd2a6-86c4-4ce7-83f2-f2661803f752
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 24
---
# 方法: ジェネリック クラスを使用する (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

*型パラメーター* を受け取るクラスは、 *ジェネリック クラス*と呼ばれます。 ジェネリック クラスを使用している場合は、このパラメーターのそれぞれに *型引数* を入力することで、ジェネリック クラスから *構築済みクラス* を生成することができます。 これで、構築済みクラス型の変数を宣言し、構築済みクラスのインスタンスを作成して、その変数に割り当てることができます。  
  
 クラスに加えて、ジェネリックの構造体、インターフェイス、プロシージャ、デリゲートを定義して利用することもできます。  
  
 次のプロシージャは、 [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] で定義されたジェネリック クラスを受け取り、そこからインスタンスを作成します。  
  
### <a name="to-use-a-class-that-takes-a-type-parameter"></a>型パラメーターを受け取るクラスを使用するには  
  
1.  ソース ファイルの先頭に [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) を含めて、<xref:System.Collections.Generic?displayProperty=fullName> 名前空間をインポートします。 これにより、<xref:System.Collections.Queue?displayProperty=fullName> などの他のキュー クラスと区別するために完全修飾しなくても <xref:System.Collections.Generic.Queue%601?displayProperty=fullName> クラスを参照できるようになります。  
  
2.  通常の方法でオブジェクトを作成し、クラス名の直後に `(Of` `type``)` を追加します。  
  
     次の例では、同じクラス (<xref:System.Collections.Generic.Queue%601?displayProperty=fullName>) を使用して、異なるデータ型の項目を保持する 2 つのキュー オブジェクトを作成しています。 項目は各キューの末尾に追加された後に削除され、各キューの先頭から項目が表示されます。  
  
     [!code-vb[VbVbalrDataTypes#9](../../../../visual-basic/language-reference/data-types/codesnippet/visualbasic/how-to-use-a-generic-class_1.vb)]  
  
## <a name="see-also"></a>関連項目  
 [データ型](../../../../visual-basic/programming-guide/language-features/data-types/index.md)   
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)   
 [言語への非依存性、および言語非依存コンポーネント](../Topic/Language%20Independence%20and%20Language-Independent%20Components.md)   
 [Of](../../../../visual-basic/language-reference/statements/of-clause.md)   
 [Imports ステートメント (.NET 名前空間および型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [方法: 複数のデータ型に同一の機能を提供できるクラスを定義する](../../../../visual-basic/programming-guide/language-features/data-types/how-to-define-a-class-that-can-provide-identical-functionality.md)   
 [反復子](../Topic/Iterators%20\(C%23%20and%20Visual%20Basic\).md)