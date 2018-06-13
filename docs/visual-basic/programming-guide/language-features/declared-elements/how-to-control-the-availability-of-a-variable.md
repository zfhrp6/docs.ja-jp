---
title: '方法: 変数の可用性を制御する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- access levels, declared elements
- Private keyword [Visual Basic], accessing variables
- access levels, variables
- Public keyword [Visual Basic], accessing variables
- Friend keyword [Visual Basic], accessing variables
- variables [Visual Basic], access level
- declared elements [Visual Basic], access level
- Protected keyword [Visual Basic], accessing variables
ms.assetid: eaf4f073-7922-43ce-ae1e-90ff376ae947
ms.openlocfilehash: 27ee5d3405ea24c0754cffa85e9b89b2ac561e42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652169"
---
# <a name="how-to-control-the-availability-of-a-variable-visual-basic"></a>方法: 変数の可用性を制御する (Visual Basic)
指定して、変数の可用性を制御するその*アクセス レベル*です。 アクセス レベルは、どのようなコードは、変数に対する読み取りまたは書き込みするアクセス許可を決定します。  
  
-   *メンバー変数*(モジュール レベルと、プロシージャの外側で定義) 既定でパブリック アクセスは、すべてのコードを見ることがアクセスできることを意味します。 アクセス修飾子を指定することによって、これを変更することができます。  
  
-   *ローカル変数*(プロシージャ内で定義) 名目上、プロシージャ内のコードだけがアクセスできますが、パブリック アクセスがあります。 ローカル変数のアクセス レベルを変更することはできませんが、それを含むプロシージャのアクセス レベルを変更することができます。  
  
 詳細については、次を参照してください。 [Visual Basic でのレベルのアクセス](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)です。  
  
## <a name="private-and-public-access"></a>プライベートとパブリックのアクセス  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-module-class-or-structure"></a>変数をモジュール、クラスまたは構造体内からのみアクセスできるようにするには  
  
1.  場所、 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)プロシージャ外ではなく、モジュール、クラス、または構造体、内部変数。  
  
2.  含める、[プライベート](../../../../visual-basic/language-reference/modifiers/private.md)キーワード、`Dim`ステートメントです。  
  
     読み取りまたはからではなく、モジュール、クラス、または構造内で任意の場所から変数への書き込みが外側にします。  
  
#### <a name="to-make-a-variable-accessible-from-any-code-that-can-see-it"></a>変数を参照できる任意のコードからアクセスできるようにするには  
  
1.  メンバー変数の場合は、配置、`Dim`変数、プロシージャの外部ではなく、モジュール、クラス、または構造体、内部のステートメント。  
  
2.  含める、[パブリック](../../../../visual-basic/language-reference/modifiers/public.md)キーワード、`Dim`ステートメントです。  
  
     読み取りまたはアセンブリと相互運用する任意のコードから変数への書き込みことができます。  
  
 - または -  
  
1.  ローカル変数では、配置、`Dim`変数、プロシージャ内のステートメント。  
  
2.  含めないでください、`Public`キーワード、`Dim`ステートメントです。  
  
     読み取りまたはからではなく、プロシージャ内で任意の場所から変数への書き込みが外側にします。  
  
## <a name="protected-and-friend-access"></a>保護されているとフレンド アクセス  
 変数をクラスおよび派生クラス、またはそのアセンブリへのアクセス レベルを制限することができます。 同じアセンブリ内の他の場所または任意の派生クラスでは、コードからへのアクセスを許可するこれらの制限の和集合を指定することもできます。 結合することでこの共用体を指定する、`Protected`と`Friend`同じ宣言内のキーワードです。  
  
#### <a name="to-make-a-variable-accessible-only-from-within-its-class-and-any-derived-classes"></a>変数をそのクラスと派生クラス内からのみアクセスできるようにするには  
  
1.  場所、`Dim`変数、プロシージャの外側ですが、クラス内のステートメント。  
  
2.  含める、 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)キーワード、`Dim`ステートメントです。  
  
     読み取りまたはからではなく、そこから派生クラス内からだけでなく、クラス内で任意の場所から変数への書き込みができる派生チェーン内のクラス外です。  
  
#### <a name="to-make-a-variable-accessible-only-from-within-the-same-assembly"></a>変数を同じアセンブリ内からのみアクセスできるようにするには  
  
1.  場所、`Dim`変数、プロシージャの外部ではなく、モジュール、クラス、または構造体、内部のステートメント。  
  
2.  含める、[フレンド](../../../../visual-basic/language-reference/modifiers/friend.md)キーワード、`Dim`ステートメントです。  
  
     読み取りまたは、モジュール、クラス、または構造内で任意の場所だけでなく、同じアセンブリ内からではなく、任意のコードからから変数への書き込みができるアセンブリの外側です。  
  
## <a name="example"></a>例  
 次の例は、変数の宣言を示しています。 `Public`、 `Protected`、 `Friend`、 `Protected Friend`、および`Private`アクセス レベル。 場合、`Dim`ステートメントがアクセス レベルを指定しますを含める必要はありません、`Dim`キーワード。  
  
```  
Public Class classForEverybody  
Protected Class classForMyHeirs  
Friend stringForThisProject As String  
Protected Friend stringForProjectAndHeirs As String  
Private numberForMeOnly As Integer  
```  
  
## <a name="net-framework-security"></a>.NET Framework セキュリティ  
 制限の厳しいアクセス レベルで、変数、悪意のあるコードが不正にする可能性が小さいそれを使用します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic でのアクセス レベル](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Dim ステートメント](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Public](../../../../visual-basic/language-reference/modifiers/public.md)  
 [Protected](../../../../visual-basic/language-reference/modifiers/protected.md)  
 [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)  
 [Private](../../../../visual-basic/language-reference/modifiers/private.md)
