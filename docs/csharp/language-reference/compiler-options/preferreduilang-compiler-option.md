---
title: -preferreduilang (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /preferreduilang
helpviewer_keywords:
- preferreduilang compiler option [C#]
- /preferreduilang compiler option [C#]
- -preferreduilang compiler option [C#]
ms.assetid: 68b2462f-6778-48d7-8052-62805fe8e02c
ms.openlocfilehash: 21a3baceb8a46723de1c633e415af0660bb41840
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33211752"
---
# <a name="-preferreduilang-c-compiler-options"></a>-preferreduilang (C# コンパイラ オプション)
`-preferreduilang` コンパイラ オプションを使うと、C# コンパイラがエラー メッセージなどの出力を表示する言語を指定できます。  
  
## <a name="syntax"></a>構文  
  
```console  
-preferreduilang: language  
```  
  
## <a name="arguments"></a>引数  
 `language`  
 コンパイラの出力に使う言語の[言語名](https://msdn.microsoft.com/library/windows/desktop/dd318696(v=vs.85).aspx)。  
  
## <a name="remarks"></a>コメント  
 `-preferreduilang` コンパイラ オプションを使うと、C# コンパイラがエラー メッセージおよびその他のコマンドライン出力に使う言語を指定できます。 言語の言語パックがインストールされていない場合は、オペレーティング システムの言語設定が代わりに使われ、エラーは報告されません。  
  
```csharp  
csc.exe -preferreduilang:ja-JP  
```  
  
## <a name="requirements"></a>必要条件  
  
## <a name="see-also"></a>参照  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
