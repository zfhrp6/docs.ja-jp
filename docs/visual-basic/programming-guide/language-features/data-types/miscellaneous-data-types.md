---
title: "Miscellaneous Data Types (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Object data type, data types"
  - "data types [Visual Basic], choosing"
ms.assetid: 64c71a12-9057-4dbf-baca-7379c4aada69
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Miscellaneous Data Types (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/developing-apps/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] には、数値や文字を対象としないデータ型が用意されています。  これらのデータ型では、Yes\/No 型や日付\/時刻型、およびオブジェクト アドレスなどの特殊なデータが処理されます。  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] データ型の side\-by\-side の比較を示す表については、「[Data Types](../../../../visual-basic/language-reference/data-types/data-type-summary.md)」を参照してください。  
  
## ブール型 \(Boolean\)  
 [Boolean Data Type](../../../../visual-basic/language-reference/data-types/boolean-data-type.md) は、`True` と `False` のいずれかに解釈される符号なしの値です。  データのサイズは、実装されているプラットフォームによって異なります。  変数に真\/偽、はい\/いいえ、オン\/オフなど 2 つの状態の値しか含まれない場合は、ブール型 \(`Boolean`\) として変数を宣言します。  
  
## 日付型 \(Date\)  
 [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) は、日付と時刻の両方の情報を保持する 64 ビットの値です。  増分は、グレゴリオ暦の西暦 1 年 1 月 1 日午前 12 時からの経過時間の 100 ナノ秒を表します。  変数に日付値、時刻値、またはその両方が含まれる場合は、日付型 \(`Date`\) として変数を宣言します。  
  
## オブジェクト型  
 [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) は、そのアプリケーション内または他のアプリケーション内にあるオブジェクト インスタンスを指す 32 ビットのアドレスです。  `Object` 変数は、アプリケーションで認識できる各オブジェクトや各データ型のデータに関連付けることができます。  これは *値型の*  どちらも `Integer` など`Boolean`構造体 `String` などのクラスから作成されるオブジェクトのインスタンスと <xref:System.Windows.Forms.Form> であると配列のインスタンスが含まれますインスタンスと  *参照型* 。  
  
 コンパイル時には判断できないクラスのインスタンスへのポインターを変数に格納する場合や、変数でさまざまなデータ型のデータを指せるようにする場合は、オブジェクト型 \(`Object`\) として変数を宣言します。  
  
 `Object` のデータ型の利点は任意のデータ型のデータを格納するために使用できます。  欠点は、実行に時間を必要とする追加の演算が行われるためアプリケーションの動作が遅くなることです。  値型に対して `Object` 変数を使用する場合は、*ボックス化*および*ボックス化解除*が必要です。  参照型に対して使用する場合は、*遅延バインディング*が必要です。  
  
## 参照  
 [Type Characters](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)   
 [Elementary Data Types](../../../../visual-basic/programming-guide/language-features/data-types/elementary-data-types.md)   
 [Numeric Data Types](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)   
 [Character Data Types](../../../../visual-basic/programming-guide/language-features/data-types/character-data-types.md)   
 [Troubleshooting Data Types](../../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)   
 [Early and Late Binding](../../../../visual-basic/programming-guide/language-features/early-late-binding/early-and-late-binding.md)