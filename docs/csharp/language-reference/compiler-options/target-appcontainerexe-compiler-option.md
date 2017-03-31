---
title: "/target:appcontainerexe (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
caps.latest.revision: 13
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 168771506692308bc9b031df5c059e58e8d190b1
ms.lasthandoff: 03/13/2017

---
# <a name="targetappcontainerexe-c-compiler-options"></a>/target:appcontainerexe (C# コンパイラ オプション)
**/target:appcontainerexe** コンパイラ オプションを使用すると、アプリケーション コンテナーで実行する必要のある Windows 実行可能ファイル (.exe) がコンパイラによって作成されます。 このオプションは [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md) に相当しますが、[!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] アプリ用に設計されています。  
  
## <a name="syntax"></a>構文  
  
```  
/target:appcontainerexe  
```  
  
## <a name="remarks"></a>コメント  
 アプリケーション コンテナーでのアプリケーションの実行を要求するために、このオプションは、[Portable Executable](http://go.microsoft.com/fwlink/p/?LinkId=236960) (PE) ファイルでビットを設定します。 このビットが設定されている場合、CreateProcess メソッドがアプリケーション コンテナー外の実行可能ファイルを起動しようとすると、エラーが発生します。  
  
 [/out](../../../csharp/language-reference/compiler-options/out-compiler-option.md) オプションを使用しない限り、出力ファイル名は [Main](../../../csharp/programming-guide/main-and-command-args/index.md) メソッドを含む入力ファイルと同じになります。  
  
 コマンド ラインで指定すると、次の **/out** オプションまたは **/target** オプションまでのすべてのファイルが、実行可能ファイルの作成に使用されます。  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>IDE でこのコンパイラ オプションを設定するには  
  
1.  **ソリューション エクスプローラー**で、プロジェクトのショートカット メニューを開き、**[プロパティ]** を選択します。  
  
2.  **[アプリケーション]** タブの **[出力の種類]** ボックスの一覧で、**[Windows ストア アプリ]** をクリックします。  
  
     このオプションは [!INCLUDE[win8_appname_long](../../../csharp/includes/win8_appname_long_md.md)] アプリケーション テンプレートでのみ使用できます。  
  
 このコンパイラ オプションをプログラムで設定する方法については、「<xref:VSLangProj80.ProjectProperties3.OutputType%2A>」を参照してください。  
  
## <a name="example"></a>例  
 次のコマンドは、アプリケーション コンテナーでのみ実行できる Windows 実行可能ファイルに `filename.cs` をコンパイルします。  
  
```  
csc /target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>関連項目  
 [/target (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)   
 [/target:winexe (C# コンパイラ オプション)](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)   
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
