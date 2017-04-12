---
title: "参照と Imports ステートメント (Visual Basic) |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references, assembly
- namespaces, assemblies
- referencing assemblies
- Imports statement, referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 283a27e7703b31a9aeed8f7e4104e89b7ff78525
ms.lasthandoff: 03/13/2017

---
# <a name="references-and-the-imports-statement-visual-basic"></a>参照と Imports ステートメント (Visual Basic)
利用できる外部のオブジェクトをプロジェクトを選択して、**参照の追加**コマンドを**プロジェクト**メニュー。 参照[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]アセンブリでは、タイプ ライブラリの詳細に説明のようなものを指すことができます。  
  
## <a name="the-imports-statement"></a>Imports ステートメント  
 アセンブリには、1 つ以上の名前空間が含まれています。 アセンブリへの参照を追加するときに追加することも、`Imports`ステートメント、モジュール内でそのアセンブリの名前空間の表示を制御するモジュールにします。 `Imports`ステートメントができるように一意の参照を指定するために必要な名前空間の部分のみを使用するスコープのコンテキストを提供します。  
  
 `Imports`ステートメントでは、次の構文。  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname`インポートされた名前空間を参照するコード内で使用できる短い名前を参照します。 `Namespace`いずれかで利用可能な名前空間、プロジェクト内の定義、または以前を通じて、プロジェクトの参照は、`Imports`ステートメントです。  
  
 モジュールは、任意の数を含めることがあります`Imports`ステートメントです。 いずれかの後に現れる必要があります`Option`存在する場合、ステートメントが、その他のコードよりも前に、です。  
  
> [!NOTE]
>  プロジェクト参照とを混同しないでください、`Imports`ステートメント、または`Declare`ステートメントです。 プロジェクト参照を指定するように、アセンブリ内のオブジェクトなど、外部のオブジェクトは使用できる[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]プロジェクトです。 `Imports`ステートメントは、プロジェクト参照へのアクセスを簡略化されますが、これらのオブジェクトへのアクセスを提供しません。 `Declare`ダイナミック リンク ライブラリ (DLL) で外部プロシージャへの参照を宣言するステートメントを使用します。  
  
## <a name="using-aliases-with-the-imports-statement"></a>Imports ステートメントを使用してエイリアスを使用します。  
 `Imports`ステートメントをやすくクラスのアクセス方法によって明示的に参照の完全修飾名を入力する必要はありません。 エイリアスを使用する名前空間の一部に過ぎませんをわかりやすい名前を割り当てることができます。 などの一部は、復帰/改行に複数の行に表示されるテキストの&1; つの原因となるシーケンス、<xref:Microsoft.VisualBasic.ControlChars>のモジュール、<xref:Microsoft.VisualBasic?displayProperty=fullName>名前空間</xref:Microsoft.VisualBasic?displayProperty=fullName></xref:Microsoft.VisualBasic.ControlChars>。 この定数を使用して、エイリアスを使わずにプログラムには、次のコードを入力する必要があります。  
  
 [!code-vb[VbVbalrApplication&#3;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports`ステートメントはすぐに次のいずれかの最初の行に常にあります`Option`モジュール内のステートメントです。 次のコード フラグメントをインポートしてのエイリアスを割り当てる方法を示しています、<xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>モジュール:</xref:Microsoft.VisualBasic.ControlChars?displayProperty=fullName>  
  
 [!code-vb[VbVbalrApplication&4;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 この名前空間への今後の参照が大幅に短くなります。  
  
 [!code-vb[VbVbalrApplication&#5;](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 場合、`Imports`ステートメントにエイリアス名を含まない、インポートされた名前空間内で定義されている要素を修飾なしのモジュールで使用できます。 エイリアス名が指定されている場合は、その名前空間内に含まれる名前の修飾子として使用するあります。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ControlChars></xref:Microsoft.VisualBasic.ControlChars>   
 <xref:Microsoft.VisualBasic></xref:Microsoft.VisualBasic>   
 [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)   
 [方法: を作成し、コマンドラインを使用してアセンブリを使用します。](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)   
 [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
