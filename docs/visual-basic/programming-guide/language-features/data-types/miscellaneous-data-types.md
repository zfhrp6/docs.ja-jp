---
title: "その他のデータ型 (Visual Basic) |Microsoft ドキュメント"
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
- Object data type, data types
- data types [Visual Basic], choosing
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
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
ms.openlocfilehash: 2de377fa9dfd7ec13cdbb9b700f8485b0c0e2106
ms.lasthandoff: 03/13/2017

---
# <a name="miscellaneous-data-types-visual-basic"></a>その他のデータ型 (Visual Basic)
[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]数値や文字を対象としていない複数のデータ型を提供します。 代わりになどを扱う特殊なデータはい/いいえ値、日付/時刻値、およびオブジェクトのアドレス。  
  
 サイド バイ サイドの比較を示す表に、[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]データ型を参照してください[データ型](../../../../visual-basic/language-reference/data-types/data-type-summary.md)します。  
  
## <a name="boolean-type"></a>ブール型  
 [ブール データ型](../../../../visual-basic/language-reference/data-types/boolean-data-type.md)いずれかとして解釈される符号なしの値は、`True`または`False`です。 データのサイズは実装されているプラットフォームに依存します。 変数は、はい/いいえ、またはオン/オフ、true または false などの&2; つの状態値のみを含めることができます、宣言として`Boolean`します。  
  
## <a name="date-type"></a>Date 型  
 [Date データ型](../../../../visual-basic/language-reference/data-types/date-data-type.md)日付と時刻の両方の情報を保持する 64 ビット値です。 増分では、グレゴリオ暦の年 1 月 1 (12時 00分 AM) 開始時からの経過時間の 100 ナノ秒を表します。 変数には、日付値、時間の値、またはその両方を含めることができます、宣言として`Date`します。  
  
## <a name="object-type"></a>オブジェクトの種類  
 [Object データ型](../../../../visual-basic/language-reference/data-types/object-data-type.md)またはその他のアプリケーションで、アプリケーション内でオブジェクトのインスタンスを指す 32 ビット アドレスです。 `Object`変数は、アプリケーションが認識されると、任意のオブジェクトまたは任意のデータ型のデータを参照できます。 両方が含まれます*値の型*など`Integer`、 `Boolean`、および構造体のインスタンスと*型を参照*であるなどのクラスから作成されたオブジェクトのインスタンスである`String`と<xref:System.Windows.Forms.Form>、インスタンスの配列</xref:System.Windows.Forms.Form>。  
  
 変数は、コンパイル時に不明なクラスのインスタンスへのポインターを格納するさまざまなデータ型のデータをポイントできる場合や、宣言として`Object`します。  
  
 利点、`Object`データ型は、任意のデータ型のデータの格納に使用ことができます。 デメリットは、実行に時間がかかると、アプリケーションの実行が遅くなる余分な処理を発生することです。 使用する場合、`Object`発生する値型の変数、*ボックス化*と*ボックス化解除*します。 参照型を使用する場合に発生する*遅延バインディング*します。  
  
## <a name="see-also"></a>関連項目  
 [型文字](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [基本データ型](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [数値データ型](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [文字データ型](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [データ型のトラブルシューティング](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [事前バインディングと遅延バインディング](../../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)
