---
title: -sdkpath
ms.date: 07/20/2015
f1_keywords:
- sdkpath
- -sdkpath
helpviewer_keywords:
- -sdkpath compiler option [Visual Basic]
- /sdkpath compiler option [Visual Basic]
- sdkpath compiler option [Visual Basic]
ms.assetid: fec8a3f1-b791-4a37-8af7-344859f8212d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 162c7d58350c381ec667e8a4cd11c03e83fcdf44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654766"
---
# <a name="-sdkpath"></a>-sdkpath
Mscorlib.dll および Microsoft.VisualBasic.dll の位置を指定します。  
  
## <a name="syntax"></a>構文  
  
```  
-sdkpath:path  
```  
  
## <a name="arguments"></a>引数  
 `path`  
 Mscorlib.dll および Microsoft.VisualBasic.dll のコンパイルを使用するのバージョンを含むディレクトリです。 読み込まれるまで、このパスは検証されません。 ディレクトリ名を引用符で囲みます ("")、スペースが含まれている場合。  
  
## <a name="remarks"></a>コメント  
 このオプションは、既定以外の場所から mscorlib.dll および Microsoft.VisualBasic.dll のファイルを読み込む Visual Basic コンパイラに指示します。 `-sdkpath`オプションで使用するように設計されました[-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)です。 [!INCLUDE[Compact](~/includes/compact-md.md)]これらの異なるバージョンを使用してサポート ライブラリを型と、デバイスが見つかりません。 言語機能は使用しないでください。  
  
> [!NOTE]
>  `-sdkpath`オプションは、Visual Studio 開発環境からは利用できません; は、コマンドラインからコンパイルするときにのみ使用します。 `-sdkpath` Visual Basic プロジェクトのデバイスが読み込まれるときに、オプションを設定します。  
  
 使用して、Visual Basic ランタイム ライブラリへの参照なしコンパイラでコンパイルする必要があることを指定することができます、`-vbruntime`コンパイラ オプション。 詳細については、次を参照してください。 [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)です。  
  
## <a name="example"></a>例  
 次のコードのコンパイル`Myfile.vb`で、[!INCLUDE[Compact](~/includes/compact-md.md)]の既定のインストール ディレクトリで見つかった Mscorlib.dll および Microsoft.VisualBasic.dll のバージョンを使用して、[!INCLUDE[Compact](~/includes/compact-md.md)]が C ドライブにします。 通常の最新バージョンを使用すると、[!INCLUDE[Compact](~/includes/compact-md.md)]です。  
  
```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb  
```  
  
## <a name="see-also"></a>関連項目  
 [Visual Basic のコマンド ライン コンパイラ](../../../visual-basic/reference/command-line-compiler/index.md)  
 [コンパイル コマンド ラインのサンプル](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [-netcf](../../../visual-basic/reference/command-line-compiler/netcf.md)  
 [-vbruntime](../../../visual-basic/reference/command-line-compiler/vbruntime.md)
