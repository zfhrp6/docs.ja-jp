---
title: 列挙型を使用する状況 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
ms.openlocfilehash: e50057e114abae9fbf05c94ef0b60cf94b033a2b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33647310"
---
# <a name="when-to-use-an-enumeration-visual-basic"></a>列挙型を使用する状況 (Visual Basic)
列挙体は、関連する定数のセットを操作する簡単な方法を提供します。 列挙をまたは`Enum`一連の値のシンボリック名を指定します。 列挙体は、データ型として扱われ、それらを使用して、変数とプロパティを使用する定数のセットを作成することができます。  
  
## <a name="when-to-use-an-enumeration"></a>列挙型を使用する状況  
 プロシージャが、限られた一連の変数を受け入れるときに、列挙体の使用を検討します。 列挙体は、わかりやすい名前を使用する場合に特に明確でわかりやすくコードでは、ようにします。  
  
 列挙体を使用する利点は次のとおりです。  
  
-   転置または番号の入力ミスによって発生したエラーが減少します。  
  
-   将来の値を変更するのには便利です。  
  
-   コードを読みやすくするので、そこにエラーが生じる可能性がある可能性が低くなります。  
  
-   前方の互換性を確保します。 列挙型をコードが後で、メンバー名に対応する値が変更された場合は失敗する可能性は低くします。  
  
## <a name="naming-enumerations"></a>列挙体の名前を付ける  
 列挙型メンバーの名前付け規則を使用します。 Visual Basic では、列挙メンバー名が検出されると、その他の参照先の型ライブラリには、同じ名前が含まれている場合に例外がスローする可能性があります。 アプリケーションまたはコンポーネントから値を識別する一意のプレフィックスを使用します。  
  
 列挙体のメンバーの場合は、する必要があります列挙名でメンバー名を修飾するか、またはを使用して、`Imports`ステートメントです。 詳細については、次を参照してください。[列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)です。  
  
## <a name="predefined-enumerations"></a>事前定義された列挙型  
 Visual Basic などの事前定義された列挙体の数の提供`FirstDayOfWeek`と`MsgBoxResult`コードを容易にします。 これらの一覧については、次を参照してください。[定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)です。  
  
## <a name="see-also"></a>関連項目  
 [方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [方法 : 列挙型のメンバーを参照する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [列挙型と名前の修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [方法: Visual Basic で列挙型を反復処理します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [方法 : 列挙値に関連付けられている文字列を確認する](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)  
 [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
