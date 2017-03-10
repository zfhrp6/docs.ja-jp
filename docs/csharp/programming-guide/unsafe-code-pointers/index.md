---
title: "アンセーフ コードとポインター (C# プログラミング ガイド) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "セキュリティ [C#]、タイプ セーフ"
  - "C# 言語、アンセーフ コード"
  - "タイプ セーフ [C#]"
  - "unsafe キーワード [C#]"
  - "アンセーフ コード [C#]"
  - "C# 言語、ポインター"
  - "ポインター [C#]、ポインターの概要"
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
caps.latest.revision: 24
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 24
---
# アンセーフ コードとポインター (C# プログラミング ガイド)
型の安全性とセキュリティを維持するために、既定では C\# はポインター演算をサポートしません。  ただし、[unsafe](../../../csharp/language-reference/keywords/unsafe.md) キーワードを使用すると、ポインターを使用できる unsafe コンテキストを定義できます。  ポインターの詳細については、「[ポインター型 \(C\# プログラミング ガイド\)](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)」を参照してください。  
  
> [!NOTE]
>  共通言語ランタイム \(CLR\) では、アンセーフ コードは検査できないコードと呼ばれます。  C\# のアンセーフ コードは、必ずしも危険ではありません。ただ CLR で安全性を検査できないコードであるというだけです。  そのため CLR は、完全に信頼できるアセンブリ内にある場合にのみ、アンセーフ コードを実行します。  アンセーフ コードを使用する場合は、セキュリティ上のリスクやポインター エラーが発生しないように注意してください。  
  
## アンセーフ コードの概要  
 アンセーフ コードには次の特性があります。  
  
-   メソッド、型、およびコード ブロックは、unsafe として定義できます。  
  
-   アンセーフ コードでアプリケーションのパフォーマンスが向上することがあります。これは、配列のバインド チェックが削除されるためです。  
  
-   アンセーフ コードは、ポインターを必要とするネイティブ関数を呼び出すときに必要です。  
  
-   アンセーフ コードを使用すると、セキュリティと安定性の面でリスクが高くなります。  
  
-   C\# でアンセーフ コードをコンパイルするには、[\/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) を指定してアプリケーションをコンパイルする必要があります。  
  
## 関連項目  
 詳細については、次のトピックを参照してください。  
  
-   [ポインター型](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [固定サイズ バッファー](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [方法 : ポインターを使用してバイトの配列をコピーする](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [安全でない](../../../csharp/language-reference/keywords/unsafe.md)  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 参照  
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)