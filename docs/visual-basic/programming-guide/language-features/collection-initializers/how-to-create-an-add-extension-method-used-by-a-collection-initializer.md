---
title: '方法: コレクション初期化子で使用される拡張メソッドを作成または追加する (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 5e35ad80037e843fd3cbd9caa68dcb2a09d707e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>方法: コレクション初期化子で使用される拡張メソッドを作成または追加する (Visual Basic)
コレクション初期化子を使用してコレクションを作成するときに、Visual Basic コンパイラはの検索、`Add`対象のコレクション型のメソッドのパラメーター、`Add`メソッド、コレクション初期化子内の値の型に一致します。 これは、`Add`メソッドを使用して、コレクション初期化子から値を持つコレクションを設定します。  
  
 一致する場合`Add`メソッドが存在して、コレクションのコードを変更することはできません、という拡張メソッドを追加する`Add`コレクション初期化子で必要とされるパラメーターを取得します。 これは、通常ジェネリック コレクションに対するコレクション初期化子を使用する場合に実行する必要があります。  
  
## <a name="example"></a>例  
 次の例は、ジェネリック拡張メソッドを追加する方法を示します<xref:System.Collections.Generic.List%601>入力型のオブジェクトを追加する、コレクション初期化子を使用できるようにする`Employee`です。 拡張メソッドでは、簡略化されたコレクションの初期化子構文を使用することができます。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a>関連項目  
 [コレクション初期化子](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [方法: コレクション初期化子を使用してコレクションを作成する](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
