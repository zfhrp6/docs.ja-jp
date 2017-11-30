---
title: /sdkpath
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- sdkpath
- /sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 876922385124db3e8db12c93c75194da83d2526c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sdkpath"></a>/sdkpath
Mscorlib.dll および Microsoft.VisualBasic.dll の位置を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
/sdkpath:path  
```  
  
## <a name="arguments"></a>引数  
 `path`  
 コンパイルに使用するには、Mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを含むディレクトリです。 読み込まれるまで、このパスは検証されません。 ディレクトリ名を引用符で囲みます ("")、スペースが含まれている場合。  
  
## <a name="remarks"></a>コメント  
 このオプションでは、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]コンパイラに既定以外の場所から Mscorlib.dll および Microsoft.VisualBasic.dll のファイルをロードします。 `/sdkpath`オプションで使用するように設計されました[/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)です。 [!INCLUDE[Compact](~/includes/compact-md.md)]これらの異なるバージョンを使用してサポート ライブラリを型と、デバイスが見つかりません。 言語機能は使用しないでください。  
  
> [!NOTE]
>  `/sdkpath`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。 `/sdkpath`場合は、オプションが設定されて、[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]デバイス プロジェクトが読み込まれています。  
  
 使用して、Visual Basic ランタイム ライブラリへの参照なしコンパイラでコンパイルする必要があることを指定することができます、`/vbruntime`コンパイラ オプション。 詳細については、次を参照してください。 [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)です。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`Myfile.vb`で、[!INCLUDE[Compact](~/includes/compact-md.md)]の既定のインストール ディレクトリで見つかった Mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを使用して、[!INCLUDE[Compact](~/includes/compact-md.md)]が C ドライブにします。 通常の最新バージョンを使用すると、[!INCLUDE[Compact](~/includes/compact-md.md)]です。  
  
```  
vbc /netcf /sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [/netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [/vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
