---
title: "(Visual Basic) 列挙型を使用する |Microsoft ドキュメント"
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
- enumerations [Visual Basic]
ms.assetid: e6e47b5b-3ed9-452d-a481-9c3fed88519a
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: f22102a2e1e7eafd7fcf4db1f46af2cc622eba70
ms.lasthandoff: 03/13/2017

---
# <a name="when-to-use-an-enumeration-visual-basic"></a>列挙型を使用する状況 (Visual Basic)
列挙体は、関連する定数のセットを操作する簡単な方法を提供します。 列挙をまたは`Enum`一連の値のシンボルの名前を指定します。 列挙体は、データ型として扱われ、それらを使用して、変数やプロパティを使用する定数のセットを作成することができます。  
  
## <a name="when-to-use-an-enumeration"></a>列挙型を使用する状況  
 プロシージャが、限られた一連の変数を受け取ったときは、列挙体の使用を検討します。 列挙体は、わかりやすい名前を使用する場合に特にわかりやすく読みやすいコードを確認します。  
  
 列挙体を使用する利点は次のとおりです。  
  
-   置き換えや数値の入力ミスによって発生したエラーを削減します。  
  
-   値は、将来変更を簡単にできます。  
  
-   簡単に理解がそこにエラーが生じる可能性がある可能性が低くなります。  
  
-   上位互換性を確認します。 列挙型をコードは、メンバーの名前に対応する値が変更された後で、エラーが発生する可能性は低くです。  
  
## <a name="naming-enumerations"></a>列挙体の名前を付ける  
 列挙型メンバーの名前付け規則を使用します。 ときに[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]列挙メンバー名の場合は、発生したその他の参照されるタイプ ライブラリには、同じ名前が含まれている場合、例外がスローされる可能性ができます。 アプリケーションまたはコンポーネントから値を識別する一意のプレフィックスを使用します。  
  
 列挙体のメンバーの場合は、する必要があります列挙型の名前でメンバー名を修飾するかを使用して、`Imports`ステートメントです。 詳細については、次を参照してください。[列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)します。  
  
## <a name="predefined-enumerations"></a>定義済み列挙型  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]などの定義済みの列挙値の数が表示`FirstDayOfWeek`と`MsgBoxResul`t、コードを容易にします。 これらの一覧を参照してください。[定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)します。  
  
## <a name="see-also"></a>関連項目  
 [方法: 列挙型を宣言](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)   
 [方法: 列挙型のメンバーを参照してください](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)   
 [列挙型と名前修飾](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)   
 [方法: Visual Basic で列挙型を反復処理します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)   
 [方法: 列挙値に関連付けられている文字列を確認します。](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)   
 [Enum ステートメント](../../../../visual-basic/language-reference/statements/enum-statement.md)   
 [定数と列挙体](../../../../visual-basic/language-reference/constants-and-enumerations.md)
