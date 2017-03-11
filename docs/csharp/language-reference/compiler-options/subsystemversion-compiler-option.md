---
title: "-subsystemversion (c# コンパイラ オプション) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# /subsystemversion (C# コンパイラ オプション)
生成された実行可能ファイルを実行できる実行可能ファイルを実行できる Windows のバージョンを決定できるサブシステムの最小バージョンを指定します。 ほとんどの場合、このオプションは、実行可能ファイルが古いバージョンの Windows では使用できない特定のセキュリティ機能を活用できます。  
  
> [!NOTE]
>  自体サブシステムを指定するには、使用、 [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) コンパイラ オプション。  
  
## <a name="syntax"></a>構文  
  
```  
/subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a>パラメーター  
 `major.minor`  
 最小値では、メジャーおよびマイナー バージョンのドット付き表記で表される、サブシステムのバージョンが必要です。 たとえば、オペレーティング システムである Windows 7 より古い場合は 6.01 にこのオプションの値を設定する場合は、このトピックの後半の表に示すようにアプリケーションを実行できないことを指定できます。 値を指定する必要があります `major` と `minor` 整数値として。  
  
 先頭ゼロで、 `minor` バージョンは、バージョンを変更しないが、後続のゼロの操作を行います。 たとえば、6.1 と 6.01、同じバージョンを参照してください。 6.10 が別のバージョン。 混乱を避けるためには 2 桁とマイナー バージョンを表現することをお勧めします。  
  
## <a name="remarks"></a>コメント  
 次の表は、Windows の一般的なサブシステムのバージョンを一覧表示します。  
  
|Windows のバージョン|サブシステムのバージョン|  
|---------------------|-----------------------|  
|Windows 2000|5.00|  
|Windows XP|5.01|  
|Windows Server 2003|5.02|  
|Windows Vista|6.00|  
|Windows 7|6.01|  
|Windows Server 2008|6.01|  
|[!INCLUDE[win8](../../../csharp/language-reference/compiler-options/includes/win8-md.md)]|6.02|  
  
## <a name="default-values"></a>既定の値  
 既定値、 **/subsystemversion** コンパイラ オプションは、以下の条件に依存します。  
  
-   既定値は次の一覧で任意のコンパイラ オプションが設定されている場合は 6.02、します。  
  
    -   [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [/platform:arm](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   MSBuild を使用している場合、既定値は 6.00 は、対象とする [!INCLUDE[net_v45](../../../csharp/language-reference/compiler-options/includes/net-v45-md.md)], 、この一覧の前に指定したコンパイラ オプションのいずれかを設定していないとします。  
  
-   既定値は、上記の条件の [なし] が true の場合、4.00 です。  
  
## <a name="setting-this-option"></a>このオプションを設定する  
 設定する、 **/subsystemversion** コンパイラ オプション Visual Studio には、.csproj ファイルを開くし、の値を指定する必要があります、 `SubsystemVersion` MSBuild XML 内のプロパティです。 Visual Studio IDE では、このオプションを設定することはできません。 詳細については、このトピックの「既定値"を参照してください。 または [MSBuild プロジェクトの共通プロパティ](/visual-studio/msbuild/common-msbuild-project-properties)します。  
  
## <a name="see-also"></a>関連項目  
 [C# コンパイラ オプション](../../../csharp/language-reference/compiler-options/index.md)