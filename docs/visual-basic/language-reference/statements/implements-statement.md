---
title: "Implements ステートメント"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 1103305ffbf5425d9a6a6a09695437968642710d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="implements-statement"></a>Implements ステートメント
1 つ以上のインターフェイス、またはインターフェイス メンバーの場合、クラスに実装する必要がありますまたはが表示される構造体の定義を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
Implements interfacename [, ...]  
-or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a>指定項目  
 `interfacename`  
 必須です。 プロパティ、プロシージャ、およびイベントは、クラスまたは構造体に対応するメンバーによって実装されるインターフェイスです。  
  
 `interfacemember`  
 必須です。 実装されるインターフェイスのメンバー。  
  
## <a name="remarks"></a>コメント  
 インターフェイスは、コレクションのプロトタイプのメンバー (プロパティ、プロシージャ、およびイベント) を表すインターフェイスをカプセル化します。 インターフェイスにメンバーの宣言のみを含めるクラスと構造体は、これらのメンバーを実装します。 詳細については、「[インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)」を参照してください。  
  
 `Implements`ステートメントの直後に続く必要があります、`Class`または`Structure`ステートメントです。  
  
 インターフェイスを実装する場合は、インターフェイスで宣言されているすべてのメンバーを実装する必要があります。 任意のメンバーを省略することは、構文エラーであると見なされます。 指定する個々 のメンバーを実装する、 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)キーワード (これとは別、`Implements`ステートメント) クラスまたは構造体のメンバーを宣言する場合。 詳細については、「[インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)」を参照してください。  
  
 クラスに使用できる[プライベート](../../../visual-basic/language-reference/modifiers/private.md)プロパティと、プロシージャが、これらのメンバーの実装が変数に実装するクラスのインスタンスとして宣言されたインターフェイスの型のキャストによってのみアクセスできます。  
  
## <a name="example"></a>例  
 次の例を使用する方法を示しています、`Implements`インターフェイスのメンバーを実装するステートメント。 という名前のインターフェイスを定義`ICustomerInfo`イベント、プロパティ、およびプロシージャを使用します。 クラス`customerInfo`インターフェイスで定義されているすべてのメンバーを実装します。  
  
 [!code-vb[VbVbalrStatements#33](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_1.vb)]  
  
 なおクラス`customerInfo`を使用して、`Implements`クラスが、一部のメンバーを実装することを示すために別のソース コード行のステートメントで、`ICustomerInfo`インターフェイスです。 クラス内の各メンバーを使用して、`Implements`そのインターフェイスのメンバーを実装することを示すために、メンバー宣言の一部としてキーワード。  
  
## <a name="example"></a>例  
 次の 2 つの手順では、前の例で実装されるインターフェイスを使用する方法を示しています。 実装をテストするには、呼び出しをプロジェクトにこれらの手順を追加、`testImplements`プロシージャです。  
  
 [!code-vb[VbVbalrStatements#34](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/implements-statement_2.vb)]  
  
## <a name="see-also"></a>関連項目  
 [Implements](../../../visual-basic/language-reference/statements/implements-clause.md)  
 [Interface ステートメント](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [インターフェイス](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
