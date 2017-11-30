---
title: "参照と Imports ステートメント (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- assemblies [Visual Basic], namespaces
- references [Visual Basic], assembly
- namespaces [Visual Basic], assemblies
- referencing assemblies
- Imports statement [Visual Basic], referencing assemblies
- assemblies [Visual Basic], references
ms.assetid: 38149bd4-0a6f-4b31-b5f8-94a8c33f1600
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 739934b65241a7846b5323d5e75446832d83e5d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="references-and-the-imports-statement-visual-basic"></a>参照と Imports ステートメント (Visual Basic)
利用できる外部オブジェクトをプロジェクトを選択して、**参照の追加**コマンドを**プロジェクト**メニュー。 参照[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]タイプ ライブラリが含まれていますが、詳細についてにと似ていますが、アセンブリを指すことができます。  
  
## <a name="the-imports-statement"></a>Imports ステートメント  
 アセンブリには、1 つまたは複数の名前空間が含まれます。 アセンブリへの参照を追加するときに追加することも、`Imports`ステートメント、モジュール内でそのアセンブリの名前空間の表示を制御するモジュールにします。 `Imports`ステートメントは、一意の参照を指定するために必要な名前空間の部分のみを使用できるスコープのコンテキストを提供します。  
  
 `Imports`ステートメントでは、次の構文。  
  
 `Imports` [`|``Aliasname` =] `Namespace`  
  
 `Aliasname`インポート済み名前空間を参照するコード内で使用できる短い名前を指します。 `Namespace`名前空間のいずれかで使用可能なプロジェクト参照をプロジェクト内で定義、または以前を通じて`Imports`ステートメントです。  
  
 モジュールは、任意の数を含めることがあります`Imports`ステートメントです。 いずれかの後に出現する必要があります`Option`ステートメント、存在する場合、その他のコードの前にします。  
  
> [!NOTE]
>  プロジェクト参照とを混同しないでください、`Imports`ステートメントまたは`Declare`ステートメントです。 プロジェクトの参照、アセンブリ内のオブジェクトなど、外部のオブジェクトを利用[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]プロジェクト。 `Imports`ステートメントは、プロジェクト参照へのアクセスを簡素化されますが、これらのオブジェクトへのアクセスを提供しません。 `Declare`ダイナミック リンク ライブラリ (DLL) で外部プロシージャへの参照を宣言するステートメントを使用します。  
  
## <a name="using-aliases-with-the-imports-statement"></a>Imports ステートメントを使用してエイリアスを使用します。  
 `Imports`ステートメント簡単にクラスのアクセス方法によって明示的に参照の完全修飾名を入力する必要があります。 エイリアスを使用する名前空間の 1 つの部分に付けるわかりやすい名前を割り当てます。 たとえばの一部は、復帰/改行シーケンスに複数の行に表示されるテキストの 1 つの原因となる、<xref:Microsoft.VisualBasic.ControlChars>内のモジュール、<xref:Microsoft.VisualBasic?displayProperty=nameWithType>名前空間。 この定数を使用して、エイリアスがなければプログラムに、次のコードを入力する必要があります。  
  
 [!code-vb[VbVbalrApplication#3](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_1.vb)]  
  
 `Imports`ステートメントはすぐに次のいずれかの最初の行を常にある`Option`モジュール内のステートメント。 次のコード フラグメントをインポートし、エイリアスを割り当てる方法を示しています、<xref:Microsoft.VisualBasic.ControlChars?displayProperty=nameWithType>モジュール。  
  
 [!code-vb[VbVbalrApplication#4](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_2.vb)]  
  
 この名前空間への今後の参照が大幅に短くなります。  
  
 [!code-vb[VbVbalrApplication#5](../../../visual-basic/programming-guide/program-structure/codesnippet/VisualBasic/references-and-the-imports-statement_3.vb)]  
  
 場合、`Imports`ステートメントは、エイリアス名を指定していない、インポートされた名前空間内で定義されている要素を修飾なしのモジュールで使用できます。 エイリアス名が指定されている場合その名前空間内に含まれる名前の修飾子として使用するあります。  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.ControlChars>  
 <xref:Microsoft.VisualBasic>  
 [NIB 方法: [参照の追加] ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)  
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [アセンブリとグローバル アセンブリ キャッシュ](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [方法: コマンド ラインを使用してアセンブリを作成および使用する](http://msdn.microsoft.com/library/70f65026-3687-4e9c-ab79-c18b97dd8be4)  
 [Imports ステートメント (.NET 名前空間および型)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
