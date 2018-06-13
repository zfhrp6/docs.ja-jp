---
title: Lc.exe (ライセンス コンパイラ)
ms.date: 03/30/2017
helpviewer_keywords:
- Lc.exe
- .licx file
- License Compiler
- control licenses [Windows Forms]
- compiling licenses file
- license file
- .licenses file
- Windows Forms, control licenses
- licensed controls [Windows Forms]
ms.assetid: 2de803b8-495e-4982-b209-19a72aba0460
ms.openlocfilehash: c5a8b38e819c323a06faad2edba586cb18d26edc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409079"
---
# <a name="lcexe-license-compiler"></a><span data-ttu-id="0b630-102">Lc.exe (ライセンス コンパイラ)</span><span class="sxs-lookup"><span data-stu-id="0b630-102">Lc.exe (License Compiler)</span></span>
<span data-ttu-id="0b630-103">ライセンス コンパイラは、ライセンス情報を含むテキスト ファイルを読み込んで、バイナリ ファイルを生成します。このバイナリ ファイルは、リソースとして共通言語ランタイムの実行可能ファイルに埋め込むことができます。</span><span class="sxs-lookup"><span data-stu-id="0b630-103">The License Compiler reads text files that contain licensing information and produces a binary file that can be embedded in a common language runtime executable as a resource.</span></span>  
  
 <span data-ttu-id="0b630-104">.licx テキスト ファイルは、ライセンスされたコントロールがフォームに追加されると、Windows フォーム デザイナーによって自動的に生成または更新されます。</span><span class="sxs-lookup"><span data-stu-id="0b630-104">A .licx text file is automatically generated or updated by the Windows Forms Designer whenever a licensed control is added to the form.</span></span> <span data-ttu-id="0b630-105">プロジェクト システムは、コンパイルの過程で、.licx テキスト ファイルを、.NET のコントロール ライセンス サポートを提供する .licenses バイナリのリソースに変換します。</span><span class="sxs-lookup"><span data-stu-id="0b630-105">As part of compilation, the project system will transform the .licx text file into a .licenses binary resource that provides support for .NET control licensing.</span></span> <span data-ttu-id="0b630-106">バイナリのリソースは、その後、プロジェクト出力に埋め込まれます。</span><span class="sxs-lookup"><span data-stu-id="0b630-106">The binary resource will then be embedded in the project output.</span></span>  
  
 <span data-ttu-id="0b630-107">プロジェクトをビルドするときにライセンス コンパイラを使用した場合は、32 ビットと 64 ビットの間のクロス コンパイルはサポートされません。</span><span class="sxs-lookup"><span data-stu-id="0b630-107">Cross compilation between 32-bit and 64-bit is not supported when you use the License Compiler when building your project.</span></span> <span data-ttu-id="0b630-108">これは、ライセンス コンパイラはアセンブリを読み込む必要があり、32 ビット アプリケーションからの 64 ビット アセンブリの読み込みおよびその逆は、許可されないためです。</span><span class="sxs-lookup"><span data-stu-id="0b630-108">This is because the License Compiler has to load assemblies, and loading 64-bit assemblies from a 32-bit application is not allowed, and vice versa.</span></span> <span data-ttu-id="0b630-109">この場合は、コマンド ラインからライセンス コンパイラを使用して手動でライセンスをコンパイルし、対応するアーキテクチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="0b630-109">In this case, use the License Compiler from the command line to compile the license manually, and specify the corresponding architecture.</span></span>  
  
 <span data-ttu-id="0b630-110">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="0b630-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="0b630-111">このツールを実行するには、開発者コマンド プロンプト (または、Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="0b630-111">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="0b630-112">詳細については、「[Visual Studio 用開発者コマンド プロンプト](../../../docs/framework/tools/developer-command-prompt-for-vs.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b630-112">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).</span></span>  
  
 <span data-ttu-id="0b630-113">コマンド プロンプトに次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="0b630-113">At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b630-114">構文</span><span class="sxs-lookup"><span data-stu-id="0b630-114">Syntax</span></span>  
  
```  
      lc /target:  
      targetPE /complist:filename [/outdir:path]  
/i:modules [/nologo] [/v]  
```  
  
|<span data-ttu-id="0b630-115">オプション</span><span class="sxs-lookup"><span data-stu-id="0b630-115">Option</span></span>|<span data-ttu-id="0b630-116">説明</span><span class="sxs-lookup"><span data-stu-id="0b630-116">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="0b630-117">**/complist:** *filename*</span><span class="sxs-lookup"><span data-stu-id="0b630-117">**/complist:** *filename*</span></span>|<span data-ttu-id="0b630-118">.licenses ファイルに組み込むライセンス付きコンポーネントの一覧を含むファイルの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="0b630-118">Specifies the name of a file that contains the list of licensed components to include in the .licenses file.</span></span> <span data-ttu-id="0b630-119">各コンポーネントを参照するにはフルネームを使用し、各行にコンポーネントを 1 つだけ指定します。</span><span class="sxs-lookup"><span data-stu-id="0b630-119">Each component is referenced using its full name with only one component per line.</span></span><br /><br /> <span data-ttu-id="0b630-120">コマンド行を使用する場合は、プロジェクトに属するフォームごとに個別のファイルを指定できます。</span><span class="sxs-lookup"><span data-stu-id="0b630-120">Command-line users can specify a separate file for each form in the project.</span></span> <span data-ttu-id="0b630-121">Lc.exe は複数の入力ファイルを受け付けて、1 つの .licenses ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="0b630-121">Lc.exe accepts multiple input files and produces a single .licenses file.</span></span>|  
|<span data-ttu-id="0b630-122">**/h****[elp]**</span><span class="sxs-lookup"><span data-stu-id="0b630-122">**/h**[**elp**]</span></span>|<span data-ttu-id="0b630-123">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="0b630-123">Displays command syntax and options for the tool.</span></span>|  
|<span data-ttu-id="0b630-124">**/i:** *module*</span><span class="sxs-lookup"><span data-stu-id="0b630-124">**/i:** *module*</span></span>|<span data-ttu-id="0b630-125">**/complist** ファイル内に一覧表示されたコンポーネントを含むモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="0b630-125">Specifies the modules that contain the components listed in the **/complist** file.</span></span> <span data-ttu-id="0b630-126">複数のモジュールを指定するには、複数の **/i** フラグを使用します。</span><span class="sxs-lookup"><span data-stu-id="0b630-126">To specify more than one module, use multiple **/i** flags.</span></span>|  
|<span data-ttu-id="0b630-127">**/nologo**</span><span class="sxs-lookup"><span data-stu-id="0b630-127">**/nologo**</span></span>|<span data-ttu-id="0b630-128">Microsoft 著作権情報を表示しません。</span><span class="sxs-lookup"><span data-stu-id="0b630-128">Suppresses the Microsoft startup banner display.</span></span>|  
|<span data-ttu-id="0b630-129">**/outdir:** *path*</span><span class="sxs-lookup"><span data-stu-id="0b630-129">**/outdir:** *path*</span></span>|<span data-ttu-id="0b630-130">出力 .licenses ファイルを格納するディレクトリを指定します。</span><span class="sxs-lookup"><span data-stu-id="0b630-130">Specifies the directory in which to place the output .licenses file.</span></span>|  
|<span data-ttu-id="0b630-131">**/target:** *targetPE*</span><span class="sxs-lookup"><span data-stu-id="0b630-131">**/target:** *targetPE*</span></span>|<span data-ttu-id="0b630-132">.licenses ファイルを生成する実行可能ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="0b630-132">Specifies the executable for which the .licenses file is being generated.</span></span>|  
|<span data-ttu-id="0b630-133">**/v**</span><span class="sxs-lookup"><span data-stu-id="0b630-133">**/v**</span></span>|<span data-ttu-id="0b630-134">詳細出力モードを指定します。コンパイルの進行状況に関する情報が表示されます。</span><span class="sxs-lookup"><span data-stu-id="0b630-134">Specifies verbose mode; displays compilation progress information.</span></span>|  
|<span data-ttu-id="0b630-135">**@** *file*</span><span class="sxs-lookup"><span data-stu-id="0b630-135">**@** *file*</span></span>|<span data-ttu-id="0b630-136">応答 (.rsp) ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="0b630-136">Specifies the response (.rsp) file.</span></span>|  
|<span data-ttu-id="0b630-137">**/?**</span><span class="sxs-lookup"><span data-stu-id="0b630-137">**/?**</span></span>|<span data-ttu-id="0b630-138">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="0b630-138">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="0b630-139">例</span><span class="sxs-lookup"><span data-stu-id="0b630-139">Example</span></span>  
  
1.  <span data-ttu-id="0b630-140">`HostApp.exe` という名前のアプリケーション内の `Samples.DLL` に格納されているライセンス付きコントロール `MyCompany.Samples.LicControl1` を使用すると *、* 次の内容を含む `HostAppLic.txt` を作成できます。</span><span class="sxs-lookup"><span data-stu-id="0b630-140">If you are using a licensed control `MyCompany.Samples.LicControl1` contained in `Samples.DLL` in an application called `HostApp.exe`*,* you can create `HostAppLic.txt` that contains the following.</span></span>  
  
    ```  
    MyCompany.Samples.LicControl1, Samples.DLL  
    ```  
  
2.  <span data-ttu-id="0b630-141">`HostApp.exe.licenses` という名前の .licenses ファイルを次のコマンドで作成します。</span><span class="sxs-lookup"><span data-stu-id="0b630-141">Create the .licenses file called `HostApp.exe.licenses` using the following command.</span></span>  
  
    ```  
    lc /target:HostApp.exe /complist:hostapplic.txt /i:Samples.DLL /outdir:c:\bindir  
    ```  
  
3.  <span data-ttu-id="0b630-142">この .licenses ファイルをリソースとして含む  `HostApp.exe` を作成します。</span><span class="sxs-lookup"><span data-stu-id="0b630-142">Build `HostApp.exe` including the .licenses file as a resource.</span></span> <span data-ttu-id="0b630-143">C# アプリケーションを作成していた場合は、次のコマンドを使用してアプリケーションを作成します。</span><span class="sxs-lookup"><span data-stu-id="0b630-143">If you were building a C# application you would use the following command to build your application.</span></span>  
  
    ```  
    csc /res:HostApp.exe.licenses /out:HostApp.exe *.cs  
    ```  
  
 <span data-ttu-id="0b630-144">`myApp.licenses`、`hostapplic.txt`、および `hostapplic2.txt` で指定されるライセンス付きコンポーネントの一覧から `hostapplic3.txt` をコンパイルするコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="0b630-144">The following command compiles `myApp.licenses` from the lists of licensed components specified by `hostapplic.txt`, `hostapplic2.txt` and `hostapplic3.txt`.</span></span> <span data-ttu-id="0b630-145">引数 `modulesList` によって、ライセンス付きコンポーネントを含むモジュールを指定します。</span><span class="sxs-lookup"><span data-stu-id="0b630-145">The `modulesList` argument specifies the modules that contain the licensed components.</span></span>  
  
```  
lc /target:myApp /complist:hostapplic.txt /complist:hostapplic2.txt /complist: hostapplic3.txt /i:modulesList  
```  
  
## <a name="response-file-example"></a><span data-ttu-id="0b630-146">応答ファイルの例</span><span class="sxs-lookup"><span data-stu-id="0b630-146">Response File Example</span></span>  
 <span data-ttu-id="0b630-147">次のリストは、`response.rsp` 応答ファイルの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="0b630-147">The following listing shows an example of a response file, `response.rsp`.</span></span> <span data-ttu-id="0b630-148">応答ファイルの詳細については、「[応答ファイル](/visualstudio/msbuild/msbuild-response-files)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="0b630-148">For more information on response files, see [Response Files](/visualstudio/msbuild/msbuild-response-files).</span></span>  
  
```  
/target:hostapp.exe  
/complist:hostapplic.txt   
/i:WFCPrj.dll   
/outdir:"C:\My Folder"  
```  
  
 <span data-ttu-id="0b630-149">次のコマンドラインで、この `response.rsp` ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="0b630-149">The following command line uses the `response.rsp` file.</span></span>  
  
```  
lc @response.rsp  
```  
  
## <a name="see-also"></a><span data-ttu-id="0b630-150">参照</span><span class="sxs-lookup"><span data-stu-id="0b630-150">See Also</span></span>  
 [<span data-ttu-id="0b630-151">ツール</span><span class="sxs-lookup"><span data-stu-id="0b630-151">Tools</span></span>](../../../docs/framework/tools/index.md)  
 [<span data-ttu-id="0b630-152">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="0b630-152">Al.exe (Assembly Linker)</span></span>](../../../docs/framework/tools/al-exe-assembly-linker.md)  
 [<span data-ttu-id="0b630-153">Visual Studio 用開発者コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="0b630-153">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)
