---
title: "方法 : RTF をプレーンテキストに変換する (C# プログラミング ガイド)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- strings [C#], converting from RTF
ms.assetid: 3b386a87-899d-4d98-bc82-a980526ddaac
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9e4c7b48467f3b260526c604fa3a36fc5d80374e
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-rtf-to-plain-text-c-programming-guide"></a>方法 : RTF をプレーンテキストに変換する (C# プログラミング ガイド)
リッチ テキスト形式 (RTF: Rich Text Format) は、1980 年代の後半にマイクロソフトが開発したドキュメント形式で、オペレーティング システム間でドキュメントを交換できます。 RTF ドキュメントの読み取りと書き込みは、Microsoft Word と WordPad のどちらでも行うことができます。 .NET Framework では、<xref:System.Windows.Forms.RichTextBox> コントロールを使用して、RTF をサポートし、ユーザーが WYSIWIG 形式でテキストに書式設定を適用できるワード プロセッサを作成できます。  
  
 <xref:System.Windows.Forms.RichTextBox> コントロールを使用して、プログラムによってドキュメントから RTF 書式指定コードを削除し、プレーンテキストに変換することもできます。 このような操作は、Windows フォームにコントロールを埋め込まなくても実行できます。  
  
### <a name="to-use-the-richtextbox-control-in-a-project"></a>プロジェクトで RichTextBox コントロールを使用するには  
  
1.  System.Windows.Forms.dll に対する参照を追加します。  
  
2.  `System.Windows.Forms` 名前空間の using ディレクティブを追加します (省略可能)。  
  
## <a name="example"></a>例  
 次の例では、サンプルの RTF ファイルをプレーンテキストに変換します。 ファイルは RTF 形式 (フォント情報など)、4 種類の Unicode 文字、および 4 個の拡張 ASCII 文字が含まれています。 このコード例では、ファイルを開き、その内容を RTF として <xref:System.Windows.Forms.RichTextBox> に渡し、テキストとして取得して、<xref:System.Windows.Forms.MessageBox> に表示したうえで、UTF-8 形式のファイルに出力します。  
  
 `MessageBox` と出力ファイルには、次のテキストが含まれています。  
  
```  
The Greek word for "psyche" is spelled ψυχή. The Greek letters are encoded in Unicode.  
These characters are from the extended ASCII character set (Windows code page 1252):  âäӑå  
```  
  
 [!code-cs[csProgGuideStrings#33](../../../csharp/programming-guide/strings/codesnippet/CSharp/how-to-convert-rtf-to-plain-text_1.cs)]  
  
 RTF 文字は 8 ビットでエンコードされますが、 ユーザーは、指定されたコード ページから、拡張 ASCII 文字のほか、Unicode 文字を指定することができます。 <xref:System.Windows.Forms.RichTextBox.Text%2A?displayProperty=fullName> プロパティは [string](../../../csharp/language-reference/keywords/string.md) 型であるため、文字は Unicode UTF-16 としてエンコードされます。 ソース RTF ドキュメントの拡張 ASCII 文字と Unicode 文字は、テキスト出力で正しくエンコードされます。  
  
 <xref:System.IO.File.WriteAllText%2A?displayProperty=fullName> メソッドを使用してテキストをディスクに書き込むと、テキストは UTF-8 としてエンコードされます (バイト オーダー マークなし)。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.RichTextBox?displayProperty=fullName>   
 [文字列](../../../csharp/programming-guide/strings/index.md)

