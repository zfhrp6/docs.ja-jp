---
title: "-codepage (C# コンパイラ オプション)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /codepage
helpviewer_keywords:
- /codepage compiler option [C#]
- codepage compiler option [C#]
- -codepage compiler option [C#]
ms.assetid: 75942989-b69a-4308-90a0-840c73d2c478
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c1181ef98ac5f335c9737771eda2b3bd9227cc9f
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="-codepage-c-compiler-options"></a>-codepage (C# コンパイラ オプション)
このオプションでは、必要とするページが、システムで使用されている現在の既定のコードページでない場合に、コンパイル時に使用するコード ページを指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-codepage:id  
```  
  
## <a name="arguments"></a>引数  
 `id`  
 コンパイル時にすべてのソース コード ファイルで使うコード ページの ID です。  
  
## <a name="remarks"></a>コメント  
 コンピューターの既定のコード ページを使わずに作成されたソース コード ファイルをコンパイルする場合は、**-codepage** オプションで、使用するコード ページを指定できます。 **-codepage** は、コンパイル時にすべてのソース コード ファイルに適用されます。  
  
 ソース コード ファイルが、コンピューターで有効なコード ページと同じものを使って作成された場合、または UNICODE か UTF-8 で作成された場合、**-codepage** を使う必要はありません。  
  
 使用しているシステムでサポートされているコード ページを確認する方法については、[GetCPInfo](https://msdn.microsoft.com/library/dd318078(VS.85).aspx) に関するページをご覧ください。  
  
 このコンパイラ オプションは Visual Studio では使用できず、プログラムで変更することはできません。  
  
## <a name="see-also"></a>参照  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)  
 [プロジェクトおよびソリューションのプロパティの管理](/visualstudio/ide/managing-project-and-solution-properties)
