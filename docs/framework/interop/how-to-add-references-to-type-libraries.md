---
title: "方法: タイプ ライブラリへの参照を追加する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "COM 相互運用機能, インポート (タイプ ライブラリの)"
  - "インポート (タイプ ライブラリの)"
  - "相互運用機能アセンブリ, 生成"
  - "タイプ ライブラリ"
ms.assetid: f5cfa6ba-cc25-4017-82cd-ba7391859113
caps.latest.revision: 12
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法: タイプ ライブラリへの参照を追加する
Visual Studio は、タイプ ライブラリに参照を追加する際に、メタデータを含む相互運用機能アセンブリを生成します。  プライマリ相互運用機能アセンブリが使用可能な場合、Visual Studio では、新しい相互運用機能アセンブリを生成する前に既存のアセンブリが使用されます。  
  
### Visual Studio でタイプ ライブラリへの参照を追加するには  
  
1.  Windows Setup.exe ファイルで COM DLL ファイルまたは EXE ファイルがインストールされない場合は、このファイルをコンピューターにインストールします。  
  
2.  **\[プロジェクト\]**、**\[参照の追加\]** の順にクリックします。  
  
3.  参照マネージャーで、**\[COM\]** をクリックします。  
  
4.  一覧からタイプ ライブラリを選択するか、.tlb ファイルを参照します。  
  
5.  **\[OK\]** をクリックします。  
  
6.  ソリューション エクスプローラーで、追加した参照のショートカット メニューを開き、**\[プロパティ\]** を選択します。  
  
7.  **\[プロパティ\]** ウィンドウで、**\[相互運用機能型の埋め込み\]** プロパティが **\[True\]** に設定されていることを確認します。  その結果、Visual Studio により、COM 型の型情報が実行可能ファイルに埋め込まれ、アプリでプライマリ相互運用機能アセンブリを配置する必要がなくなります。  
  
> [!NOTE]
>  メニュー オプションおよびダイアログ ボックス オプションは、使用中の Visula Studio のバージョンによって異なる場合があります。  
  
### コマンド ライン コンパイルのために参照をタイプ ライブラリに追加するには  
  
1.  相互運用機能アセンブリを生成します \(「[方法: 相互運用機能アセンブリをタイプ ライブラリから生成する](../../../docs/framework/interop/how-to-generate-interop-assemblies-from-type-libraries.md)」を参照\)。  
  
2.  相互運用機能アセンブリ名を使って「[\/link \(Link to COM Assembly\)](../Topic/-link%20\(C%23%20Compiler%20Options\).md)」または「[\/link](../Topic/-link%20\(Visual%20Basic\).md)」コンパイラ オプションを使用し、COM 型の型情報を実行可能ファイルに埋め込みます。  
  
## 参照  
 [タイプ ライブラリのアセンブリとしてのインポート](../../../docs/framework/interop/importing-a-type-library-as-an-assembly.md)   
 [.NET Framework への COM コンポーネントの公開](../../../docs/framework/interop/exposing-com-components.md)   
 [チュートリアル: Microsoft Office アセンブリからの型情報の埋め込み](../Topic/Walkthrough:%20Embedding%20Type%20Information%20from%20Microsoft%20Office%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [チュートリアル: マネージ アセンブリからの型の埋め込み](../Topic/Walkthrough:%20Embedding%20Types%20from%20Managed%20Assemblies%20\(C%23%20and%20Visual%20Basic\).md)   
 [\/link \(Link to COM Assembly\)](../Topic/-link%20\(C%23%20Compiler%20Options\).md)   
 [\/link](../Topic/-link%20\(Visual%20Basic\).md)