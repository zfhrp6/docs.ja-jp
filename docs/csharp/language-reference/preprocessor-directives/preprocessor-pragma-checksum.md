---
title: "#<a name=\"pragma-checksum-c-reference--microsoft-docs\"></a>#pragma checksum (C# リファレンス) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#pragma checksum'
dev_langs:
- CSharp
helpviewer_keywords:
- '#pragma checksum [C#]'
ms.assetid: 3673e4ca-6098-4ec1-890f-8fceb2a794a2
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 31905a37f09db5f5192123f0118252fbe8b02eff
ms.openlocfilehash: acb554a757886d1924fa7ef69814b98b3b440871
ms.contentlocale: ja-jp
ms.lasthandoff: 06/15/2017

---
# <a name="pragma-checksum-c-reference"></a>#pragma checksum (C# リファレンス)
[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] ページのデバッグに使用するソース ファイルのチェックサムを生成します。  
  
## <a name="syntax"></a>構文  
  
```csharp
#pragma checksum "filename" "{guid}" "checksum bytes"  
```  
  
#### <a name="parameters"></a>パラメーター  
 `"filename"`  
 変更または更新を監視する必要があるファイルの名前。  
  
 `"{guid}"`  
 ファイルのグローバル一意識別子 (GUID)。  
  
 `"checksum_bytes"`  
 チェックサムのバイト数を表す 16 進数の文字列。 偶数の 16 進数である必要があります。 奇数の数値を指定すると、コンパイル時に警告が出力され、ディレクティブが無視されます。  
  
## <a name="remarks"></a>コメント  
 Visual Studio デバッガーは、常に正しいソースを検出するために、チェックサムを使用します。 コンパイラはソース ファイルのチェックサムを計算し、プログラム データベース (PDB) ファイルに結果を出力します。 デバッガーは、その PDB ファイルを使用して、ソース ファイルについて計算したチェックサムと比較します。  
  
 このソリューションは [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] プロジェクトには使用できません。それは計算されたチェックサムは、.aspx ファイルではなく、生成されたソース ファイルを対象としているためです。 この問題に対応するため、`#pragma checksum` によって [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] ページのチェックサムがサポートされています。  
  
 [!INCLUDE[csprcs](~/includes/csprcs-md.md)] で [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] プロジェクトを作成すると、生成されるソース ファイルにソースの生成元である .aspx ファイルのチェックサムが含められます。 コンパイラは、この情報を PDB ファイルに書き込みます。  
  
 ファイルに `#pragma checksum` ディレクティブが見つからない場合、コンパイラはチェックサムを計算し、PDB ファイルにその値を書き込みます。  
  
## <a name="example"></a>例  
  
```csharp
class TestClass  
{  
    static int Main()  
    {  
        #pragma checksum "file.cs" "{3673e4ca-6098-4ec1-890f-8fceb2a794a2}" "{012345678AB}" // New checksum  
    }  
}  
```  
  
## <a name="see-also"></a>関連項目  
 [C# リファレンス](../../../csharp/language-reference/index.md)   
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C# プリプロセッサ ディレクティブ](../../../csharp/language-reference/preprocessor-directives/index.md)

