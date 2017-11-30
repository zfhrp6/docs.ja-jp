---
title: "その他のデータ型 (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Object data type [Visual Basic], data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b6bb86bb6d203aa4e6bdded27a4cb78a8155ddec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="miscellaneous-data-types-visual-basic"></a>その他のデータ型 (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]数字や文字を対象とされているいくつかのデータ型を提供します。 代わりが扱う特化されたデータなど、はい/いいえ値、日付/時刻値、およびオブジェクトのアドレス。  
  
 サイド バイ サイドの比較を示す表に、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]データ型を参照してください[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)です。  
  
## <a name="boolean-type"></a>ブール型  
 [ブールのデータ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)いずれかとして解釈される符号なしの値は、`True`または`False`です。 データのサイズは実装されているプラットフォームに依存します。 場合は、変数は、はい/いいえ、またはオン/オフ、true または false などの 2 つの状態値のみを含めることができます、宣言として`Boolean`です。  
  
## <a name="date-type"></a>日付型  
 [Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)日付と時刻の両方の情報を保持する 64 ビット値です。 各インクリメントは、グレゴリオ暦カレンダーにおける年 1 月 1 (12時 00分 AM) の開始以降の経過時間を 100 ナノ秒を表します。 場合は、変数には、日付の値、時間の値、またはその両方を含めることができます、宣言として`Date`です。  
  
## <a name="object-type"></a>オブジェクトの種類  
 [オブジェクト データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)アプリケーション内で、またはその他のアプリケーションでのオブジェクト インスタンスを指す 32 ビット アドレスです。 `Object`変数は、アプリケーションが認識されると、任意のオブジェクトや任意のデータ型のデータに参照できます。 両方が含まれます*値の型*など`Integer`、 `Boolean`、および構造体のインスタンスと*型参照*、オブジェクトなどのクラスから作成されたのインスタンスは`String`と<xref:System.Windows.Forms.Form>のインスタンスの配列。  
  
 変数が分かっていなければ、コンパイル時に、クラスのインスタンスへのポインターを格納するさまざまなデータ型のデータを指すことができる場合や、として宣言`Object`です。  
  
 利点、`Object`データ型が使用できる、任意のデータ型のデータを格納します。 欠点は、実行時間がかかるし、アプリケーションの実行速度が遅くする余分な処理が発生することです。 使用する場合、`Object`発生する値の型の変数、*ボックス化*と*アンボックス*です。 で参照型を使用する場合に発生する*遅延バインディング*です。  
  
## <a name="see-also"></a>関連項目  
 [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)  
 [数値のデータ型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [文字データ型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)  
 [トラブルシューティング (データ型)](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
