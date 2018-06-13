---
title: プロシージャのオーバーロード (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- signatures
- Overloads keyword [Visual Basic]
- hiding by signature
- Visual Basic code, procedures
- procedures [Visual Basic], signatures for
- procedures [Visual Basic], overloading
- procedures [Visual Basic], multiple versions
- parameters [Visual Basic], lists
- signatures [Visual Basic], procedure
- parameter lists [Visual Basic]
- Visual Basic code, parameter lists
- Shadows keyword [Visual Basic]
- procedure overloading
- procedures [Visual Basic], parameter lists
ms.assetid: fbc7fb18-e3b2-48b6-b554-64c00ed09d2a
ms.openlocfilehash: 0d1f2c4d8c88922659b3d91ed41d5e760e6e5233
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653915"
---
# <a name="procedure-overloading-visual-basic"></a>プロシージャのオーバーロード (Visual Basic)
*オーバー ロード*プロシージャでは、異なるパラメーター リストが同じ名前を使用して、複数のバージョンでそれを定義することを意味します。 オーバー ロードの目的では、名前で区別することがなく密接に関連するいくつかのバージョンのプロシージャを定義します。 こうと、パラメーター リストを変更します。  
  
## <a name="overloading-rules"></a>オーバー ロードの規則  
 プロシージャをオーバー ロードする場合は、次の規則が適用されます。  
  
-   **同じ名前**です。 各オーバー ロードされたバージョンでは、同じプロシージャ名を使用する必要があります。  
  
-   **異なるシグネチャ**です。 各オーバー ロードされたバージョンは、次のうちの少なくとも 1 つにその他のすべてのオーバー ロードされたバージョンと異なって必要があります。  
  
    -   パラメーターの数  
  
    -   パラメーターの順序  
  
    -   パラメーターのデータ型  
  
    -   型パラメーター (ジェネリック プロシージャの場合) の数  
  
    -   戻り値の型 (変換演算子) の場合のみ  
  
     プロシージャ名と前の項目は、総称、*署名*プロシージャのです。 オーバー ロードされたプロシージャを呼び出すときに、コンパイラは、呼び出しが、定義を正しくと一致することを確認するのに署名を使用します。  
  
-   **署名に含まれない項目**です。 シグネチャを変更せず、プロシージャをオーバー ロードすることはできません。 具体的には、プロシージャをオーバー ロードするだけで、次の項目には、1 つ以上ことはできません。  
  
    -   プロシージャ修飾子キーワードなど`Public`、 `Shared`、および `Static`  
  
    -   パラメーターまたは型のパラメーター名  
  
    -   型パラメーターの制約 (ジェネリック プロシージャ) の場合  
  
    -   パラメーター修飾子キーワードなど`ByRef`と `Optional`  
  
    -   値を返すかどうか  
  
    -   (変換演算子) を除く、戻り値のデータ型  
  
     上記のリスト内の項目は、シグネチャの一部ではありません。 オーバー ロードされたバージョンを区別するために、使用することはできません、それぞれのシグネチャによって区別されるオーバー ロードされたバージョン間でそれらを変更できます。  
  
-   **遅延バインディング引数**です。 オーバー ロードされたバージョンに遅延バインディング オブジェクト変数を渡す場合は、適切なパラメーターとしてを宣言する必要があります<xref:System.Object>です。  
  
## <a name="multiple-versions-of-a-procedure"></a>プロシージャの複数のバージョン  
 作成するいるとすると、`Sub`して、顧客の残高に対してトランザクションをポストする手順をしたい名前で、またはアカウント数によって、顧客を参照することです。 これに合わせてを定義できます 2 つの異なる`Sub`例を次の手順。  
  
 [!code-vb[VbVbcnProcedures#73](./codesnippet/VisualBasic/procedure-overloading_1.vb)]  
  
### <a name="overloaded-versions"></a>オーバー ロードされたバージョン  
 代わりに、1 つのプロシージャ名をオーバー ロードを開始します。 使用することができます、[オーバー ロード](../../../../visual-basic/language-reference/modifiers/overloads.md)キーワードを次のように各パラメーター一覧については、プロシージャのバージョンを定義します。  
  
 [!code-vb[VbVbcnProcedures#72](./codesnippet/VisualBasic/procedure-overloading_2.vb)]  
  
#### <a name="additional-overloads"></a>オーバー ロードを追加  
 いずれかでトランザクションの量をそのまま使用したい場合`Decimal`または`Single`、オーバー ロードすることがさらに`post`このバリエーションに使用できるようにします。 これを行った場合、前の例でオーバー ロードの各グループにする必要が 4 つ`Sub`4 つの異なるシグネチャを持つが、同じ名前のすべての手順です。  
  
## <a name="advantages-of-overloading"></a>オーバー ロードの利点  
 プロシージャのオーバー ロードの利点は、呼び出しの柔軟性にです。 使用する、`post`プロシージャで宣言されている前の例では、呼び出し元のコードは、いずれかとして、顧客 id を取得できます、`String`または`Integer`、どちらの場合、同じプロシージャを呼び出すとします。 次に例を示します。  
  
 [!code-vb[VbVbcnProcedures#56](./codesnippet/VisualBasic/procedure-overloading_3.vb)]  
  
 [!code-vb[VbVbcnProcedures#57](./codesnippet/VisualBasic/procedure-overloading_4.vb)]  
  
## <a name="see-also"></a>関連項目  
 [手順](./index.md)  
 [方法 : プロシージャの複数のバージョンを定義する](./how-to-define-multiple-versions-of-a-procedure.md)  
 [方法 : オーバーロードされたプロシージャを呼び出す](./how-to-call-an-overloaded-procedure.md)  
 [方法 : 省略可能なパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-optional-parameters.md)  
 [方法 : 不特定数のパラメーターを受け取るプロシージャをオーバーロードする](./how-to-overload-a-procedure-that-takes-an-indefinite-number-of-parameters.md)  
 [プロシージャのオーバーロードに関する注意事項](./considerations-in-overloading-procedures.md)  
 [オーバーロードの解決](./overload-resolution.md)  
 [オーバーロード](../../../../visual-basic/language-reference/modifiers/overloads.md)  
 [Visual Basic におけるジェネリック型](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
