---
title: '方法: コマンド ライン引数を表示する (C# プログラミング ガイド)'
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 7b9e488e84c78c8fdbf64431f42ea5797fdca916
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33334137"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>方法: コマンド ライン引数を表示する (C# プログラミング ガイド)
実行可能ファイルに対してコマンド ラインで指定した引数には、省略可能なパラメーターを介して `Main` からアクセスできます。 引数は、文字列の配列の形式で指定します。 配列の各要素には、1 つの引数が格納されます。 引数間の空白は削除されます。 たとえば、架空の実行可能ファイルを呼び出すためのコマンド ラインの例を次に示します。  
  
|コマンドラインでの入力|Main に渡される文字列の配列|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe one two**|"one"<br /><br /> "two"|  
|**executable.exe "one two" three**|"one two"<br /><br /> "three"|  
  
> [!NOTE]
>  Visual Studio でアプリケーションを実行する場合は、[[デバッグ] ページ (プロジェクト デザイナー)](/visualstudio/ide/reference/debug-page-project-designer) でコマンド ライン引数を指定できます。  
  
## <a name="example"></a>例  
 この例は、コマンド ライン アプリケーションに渡されるコマンド ライン引数を示しています。 次の出力は、上の表の最初のエントリに対するものです。  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a>参照  
 [C# プログラミング ガイド](../../../csharp/programming-guide/index.md)  
 [csc.exe を使用したコマンド ラインからのビルド](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Main() とコマンド ライン引数](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [方法: foreach を使用してコマンド ライン引数にアクセスする](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Main() の戻り値](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
