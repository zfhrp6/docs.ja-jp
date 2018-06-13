---
title: 型の値&#39; &lt;typename1&gt; &#39;に変換できない&#39; &lt;typename2&gt; &#39; (複数のファイル参照)
ms.date: 07/20/2015
f1_keywords:
- vbc30961
- bc30961
helpviewer_keywords:
- BC30961
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
ms.openlocfilehash: 41c18160be9b546f8b525376fa06bc0eca6c117a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603692"
---
# <a name="value-of-type-39lttypename1gt39-cannot-be-converted-to-39lttypename2gt39-multiple-file-references"></a>型の値&#39; &lt;typename1&gt; &#39;に変換できない&#39; &lt;typename2&gt; &#39; (複数のファイル参照)
型の値 '\<typename1 >' に変換できません。'\<typename2 >' です。 型の不一致へのファイル参照を混在させる可能性があります '\<filepath1 >' プロジェクトで'\<projectname1 >' へのファイル参照を '\<filepath2 >' プロジェクトで'\<projectname2 >' です。 両方のアセンブリが同一である場合は、これらの参照を同じ場所から参照するように置き換えてください。  
  
 状況では、プロジェクトは、1 つ以上のファイル参照アセンブリをコンパイラは、1 つの型を別に変換できることを保証できません。  
  
 それぞれのファイル参照は、ファイルのパスと (通常は DLL ファイル) のプロジェクトの出力ファイルの名前を指定します。 コンパイラは、出力ファイルが、同じソースから取得することや、同じアセンブリの同じバージョンを表すことを保証できません。 そのため、その種類別の参照では、同じの型またはも、あるは、その他に変換できることは保証できません。  
  
 参照アセンブリが同じアセンブリ id を持つことがわかっている場合は、1 つのファイルの参照を使用できます。 *アセンブリ ID* には、アセンブリの名前、バージョン、公開キー (存在する場合)、およびカルチャが含まれます。 この情報はアセンブリを一意に識別します。  
  
 **エラー ID:** BC30961  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
-   参照されるアセンブリのアセンブリ id が同じ場合は、削除するか、1 つのファイル参照のみがあるように、ファイル参照のいずれかを置き換えます。  
  
-   参照アセンブリが同じアセンブリ id を持たない場合は、1 つのもう一方の型に型変換を行いませんようにコードを変更します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic での型変換](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [プロジェクト内の参照の管理](/visualstudio/ide/managing-references-in-a-project)  
 
