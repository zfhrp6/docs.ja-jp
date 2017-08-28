---
title: "方法 : レガシ エンコーディングと Unicode の間で変換を行う (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#], legacy to unicode encoding
- strings [C#], converting between encodings
ms.assetid: 4eed7d8e-47ab-4a7c-8b95-9645a0ef000b
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: a016f4ab7de25eec408243cb9b467f9255556bba
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-between-legacy-encodings-and-unicode-c-programming-guide"></a>方法 : レガシ エンコーディングと Unicode の間で変換を行う (C# プログラミング ガイド)
C# では、メモリ内の文字列はすべて Unicode (UTF-16) としてエンコードされます。 データをストレージから `string` オブジェクトに取り込むと、そのデータは UTF-16 に自動的に変換されます。 データに含まれるのが 0 ～ 127 の ASCII 値のみの場合は、変換の際にユーザー側が特別な処理を実行する必要はありません。 ただし、ソース テキストに拡張 ASCII バイト値 (128 ～ 255) が含まれる場合、既定では、現在のコード ページに従って拡張文字が解釈されます。 ソース テキストが別のコード ページに従って解釈されるように指定するには、次の例に示すように、<xref:System.Text.Encoding?displayProperty=fullName> クラスを使用します。  
  
## <a name="example"></a>例  
 次の例は、8 ビット ASCII でエンコードされているテキスト ファイルを変換し、Windows コード ページ 737 に従ってソース テキストを解釈する方法を示しています。  
  
 [!code-cs[csProgGuideStrings#34](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-between-legacy-encodings-and-unicode_1.cs)]  
  
## <a name="see-also"></a>関連項目  
 [文字列](../../../csharp/programming-guide/strings/index.md)

