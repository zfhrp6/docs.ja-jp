---
title: "Type &#39;&lt;typename&gt;&#39; is not defined | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30002"
  - "bc30002"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30002"
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# Type &#39;&lt;typename&gt;&#39; is not defined
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

ステートメントは未定義の型を参照しました。  型は、`Enum`、`Structure`、`Class`、`Interface` などの宣言ステートメントで定義できます。  
  
 **Error ID:** BC30002  
  
### このエラーを解決するには  
  
-   型定義とその参照の両方で同じスペルを使用しているかどうかを確認します。  
  
-   参照から型定義にアクセスできるかどうかを確認します。  たとえば、型が別のモジュール内にあって `Private` として宣言されている場合は、型定義を参照元のモジュールに移動するか、型を `Public` として宣言します。  
  
-   型の名前空間がプロジェクト内で再定義されていないかどうかを確認します。  再定義されていた場合は、`Global` キーワードを使用して型名を完全修飾します。  たとえば、プロジェクトで `System` という名前空間が定義されている場合、<xref:System.Object?displayProperty=fullName> 型にアクセスするには、`Global` キーワードを使って `Global.System.Object` のように完全修飾する必要があります。  
  
-   型は定義されていても、型が定義されているオブジェクト ライブラリまたはタイプ ライブラリが [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] に登録されていない場合は、**\[プロジェクト\]** メニューの **\[参照の追加\]** をクリックし、適切なオブジェクト ライブラリまたはタイプ ライブラリを選択します。  
  
-   対象とする .NET Framework プロファイルの一部であるアセンブリに型が存在するかどうかを確認します。  詳細については、「[.NET Framework を対象とするエラーのトラブルシューティング](/visual-studio/msbuild/troubleshooting-dotnet-framework-targeting-errors)」を参照してください。  
  
## 参照  
 [Visual Basic における名前空間](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Enum Statement](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Structure Statement](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Class Statement](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Interface Statement](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [プロジェクト内の参照の管理](/visual-studio/ide/managing-references-in-a-project)