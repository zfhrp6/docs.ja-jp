---
title: "-subsystemversion (C# コンパイラ オプション) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
caps.latest.revision: 19
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8766904cad739b29c7dfe80b29305ea2b3bd2e6f
ms.lasthandoff: 03/13/2017

---
# <a name="subsystemversion-c-compiler-options"></a>/subsystemversion (C# コンパイラ オプション)
生成された実行可能ファイルが動作できるサブシステムの最小バージョンを指定します。これにより、実行可能ファイルが動作できる Windows のバージョンが決まります。 通常、このオプションを指定することで、実行可能ファイルが、Windows の以前のバージョンでは使用できない特定のセキュリティ機能を利用できるようになります。  
  
> [!NOTE]
>  サブシステム自体を指定するには、[/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) のコンパイラ オプションを使用します。  
  
## <a name="syntax"></a>構文  
  
```  
/subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a>パラメーター  
 `major.minor`  
 サブシステムに必要な最小バージョン。メジャー バージョンおよびマイナー バージョンのドット表記で表されます。 たとえば、このオプションの値を 6.01 に設定すると、Windows 7 より古いオペレーティング システムではアプリケーションを実行できないように指定できます (このトピックの以下の表を参照)。 `major` と `minor` の値を整数で指定する必要があります。  
  
 `minor` バージョンでは、前に配置されるゼロによってバージョンが変更されることはありませんが、後ろにゼロが付くとバージョンが変わります。 たとえば、6.1 と 6.01 は同じバージョンを示しますが、6.10 は異なるバージョンを示します。 混乱を避けるため、マイナー バージョンには 2 桁の数値を使用することをお勧めします。  
  
## <a name="remarks"></a>コメント  
 次の表は、Windows の一般的なサブシステムのバージョンを示しています。  
  
|Windows のバージョン|サブシステムのバージョン|  
|---------------------|-----------------------|  
|Windows 2000|5.00|  
|Windows XP|5.01|  
|Windows Server 2003|5.02|  
|Windows Vista|6.00|  
|Windows 7|6.01|  
|Windows Server 2008|6.01|  
|[!INCLUDE[win8](../../../csharp/language-reference/compiler-options/includes/win8_md.md)]|6.02|  
  
## <a name="default-values"></a>既定の値  
 **/subsystemversion** コンパイラ オプションの既定値は条件によって異なります。その条件を次に示します。  
  
-   次のコンパイラ オプションのいずれかが設定されている場合、既定値は 6.02 です。  
  
    -   [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [/platform:arm](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   MSBuild を使用しており、[!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net_v45_md.md)] が対象で、さらにこの一覧で前に指定したコンパイラ オプションを設定していない場合、既定値は 6.00 です。  
  
-   上記の条件がどれも当てはまらない場合、既定値は 4.00 です。  
  
## <a name="setting-this-option"></a>このオプションを設定する  
 Visual Studio で **/subsystemversion** コンパイラ オプションを設定するには、.csproj ファイルを開き、MSBuild XML で `SubsystemVersion` プロパティの値を指定する必要があります。 Visual Studio IDE でこのオプションを設定することはできません。 詳細については、このトピックの「既定値」または「[MSBuild プロジェクトの共通プロパティ](https://docs.microsoft.com/visualstudio/msbuild/common-msbuild-project-properties)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)
