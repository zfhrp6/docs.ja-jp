---
title: -codepage (Visual Basic)
ms.date: 03/09/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -codepage compiler option [Visual Basic]
- codepage compiler option [Visual Basic]
- -codepage compiler option [Visual Basic]
ms.assetid: be36ec33-6800-4505-838c-4124564f5cc9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 736b35f51657aa7b21a6a077d70f5e9ff0d4fb85
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2018
---
# <a name="-codepage-visual-basic"></a>-codepage (Visual Basic)
コンパイルですべてのソース コード ファイルに使用するコード ページを指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-codepage:id  
```  
  
## <a name="arguments"></a>引数  
  
|用語|定義|  
|---|---|  
|`id`|必須。 コンパイラによって指定されたコード ページを使用して`id`ソース ファイルのエンコーディングを解釈します。|  
  
## <a name="remarks"></a>コメント  
 使用することができます、特定のエンコードで保存されたソース コードをコンパイルする`-codepage`するコード ページを使用する必要がありますを指定します。 `-codepage`オプションは、コンパイル時にすべてのソース コード ファイルに適用されます。 詳細については、次を参照してください。 [.NET Framework の文字エンコーディング](http://msdn.microsoft.com/library/bf6d9823-4c2d-48af-b280-919c5af66ae9)です。  
  
 `-codepage`シグネチャを持つ現在の ANSI コード ページ、Unicode または utf-8 を使用して、ソース コード ファイルを保存した場合、オプションは必要ありません。 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] ユーザーで他のエンコーディングを指定しない限りは、既定では、現在の ANSI コード ページですべてのソース コード ファイルを保存、**エンコード** ダイアログ ボックス。 [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] 使用して、**エンコード** ダイアログ ボックスを開くにはソース コード ファイルを別のコード ページを保存します。  
  
> [!NOTE]
>  `-codepage`オプションは内から使用できません、[!INCLUDE[vsprvs](~/includes/vsprvs-md.md)]開発環境は、コマンドラインからコンパイルするときにのみ使用します。  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)
