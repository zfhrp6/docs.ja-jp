---
title: "ネイティブ相互運用性"
description: ".Net のネイティブ コンポーネントとやり取りする方法を説明します。"
keywords: .NET, .NET Core
author: blackdwarf
ms.author: ronpet
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3c357112-35fb-44ba-a07b-6a1c140370ac
ms.openlocfilehash: 9652986491f087b8fa175e2b4041063c71211178
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="native-interoperability"></a><span data-ttu-id="f3828-104">ネイティブ相互運用性</span><span class="sxs-lookup"><span data-stu-id="f3828-104">Native Interoperability</span></span>

<span data-ttu-id="f3828-105">このドキュメントでは、.NET で使用可能な "ネイティブ相互運用性" を実行する 3 つのすべての方法についてもう少し深く掘り下げます。</span><span class="sxs-lookup"><span data-stu-id="f3828-105">In this document, we will dive a little bit deeper into all three ways of doing "native interoperability" that are available using .NET.</span></span>

<span data-ttu-id="f3828-106">ネイティブ コードを呼び出す理由はいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="f3828-106">There are a few of reasons why you would want to call into native code:</span></span>

*   <span data-ttu-id="f3828-107">オペレーティング システムには、マネージ クラス ライブラリに存在しない大量の API が付属しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-107">Operating Systems come with a large volume of APIs that are not present in the managed class libraries.</span></span> <span data-ttu-id="f3828-108">この主な例には、ハードウェアまたはオペレーティング システム管理機能へのアクセスがあります。</span><span class="sxs-lookup"><span data-stu-id="f3828-108">A prime example for this would be access to hardware or operating system management functions.</span></span>
*   <span data-ttu-id="f3828-109">C スタイル ABI (ネイティブ ABI) があるか、または生成できるその他のコンポーネントと通信します。</span><span class="sxs-lookup"><span data-stu-id="f3828-109">Communicating with other components that have or can produce C-style ABIs (native ABIs).</span></span> <span data-ttu-id="f3828-110">これはたとえば、[Java ネイティブ インターフェイス (JNI)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) によって公開されている Java コードまたはネイティブ コンポーネントを生成できる他のマネージ言語を対象とします。</span><span class="sxs-lookup"><span data-stu-id="f3828-110">This covers, for example, Java code that is exposed via [Java Native Interface (JNI)](http://docs.oracle.com/javase/8/docs/technotes/guides/jni/) or any other managed language that could produce a native component.</span></span>
*   <span data-ttu-id="f3828-111">Windows では、Microsoft Office スイートなどのインストールされるソフトウェアのほとんどが、それらのプログラムを表し、開発者が自動化したり、使用したりできる COM コンポーネントを登録します。</span><span class="sxs-lookup"><span data-stu-id="f3828-111">On Windows, most of the software that gets installed, such as Microsoft Office suite, registers COM components that represent their programs and allow developers to automate them or use them.</span></span> <span data-ttu-id="f3828-112">これも、ネイティブ相互運用性を必要とします。</span><span class="sxs-lookup"><span data-stu-id="f3828-112">This also requires native interoperability.</span></span>

<span data-ttu-id="f3828-113">もちろん、上の一覧は、開発者がネイティブ コンポーネントとやり取りしたいと考える、またはその必要があるすべての可能性のある状況やシナリオを取り上げていません。</span><span class="sxs-lookup"><span data-stu-id="f3828-113">Of course, the list above does not cover all of the potential situations and scenarios in which the developer would want/like/need to interface with native components.</span></span> <span data-ttu-id="f3828-114">たとえば、.NET クラス ライブラリは、ネイティブ相互運用性サポートを使用して、コンソールのサポートと操作、ファイル システムのアクセスなど、そのかなりの数の API を実装しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-114">.NET class library, for instance, uses the native interoperability support to implement a fair number of its APIs, like console support and manipulation, file system access and others.</span></span> <span data-ttu-id="f3828-115">ただし、それを必要とする場合に、オプションがあることに注意することが重要です。</span><span class="sxs-lookup"><span data-stu-id="f3828-115">However, it is important to note that there is an option, should one need it.</span></span>

> [!NOTE]
> <span data-ttu-id="f3828-116">このドキュメントのほとんどの例は、.NET Core でサポートされる 3 つすべてのプラットフォーム (Windows、Linux、macOS) について提示しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-116">Most of the examples in this document will be presented for all three supported platforms for .NET Core (Windows, Linux and macOS).</span></span> <span data-ttu-id="f3828-117">ただし、短い解説的な例については、Windows ファイル名と拡張子 (つまり、ライブラリの場合は "dll") を使用する 1 つのサンプルだけを示します。</span><span class="sxs-lookup"><span data-stu-id="f3828-117">However, for some short and illustrative examples, just one sample is shown that uses Windows filenames and extensions (that is, "dll" for libraries).</span></span> <span data-ttu-id="f3828-118">これは、それらの機能が Linux や macOS で使用できないわけではなく、単に便宜上のためにのみそうしています。</span><span class="sxs-lookup"><span data-stu-id="f3828-118">This does not mean that those features are not available on Linux or macOS, it was done merely for convenience sake.</span></span>

## <a name="platform-invoke-pinvoke"></a><span data-ttu-id="f3828-119">プラットフォーム呼び出し (P/Invoke)</span><span class="sxs-lookup"><span data-stu-id="f3828-119">Platform Invoke (P/Invoke)</span></span>

<span data-ttu-id="f3828-120">P/invoke は、アンマネージ ライブラリ内の構造体、コールバック、および関数をマネージ コードからアクセスできるようにするテクノロジです。</span><span class="sxs-lookup"><span data-stu-id="f3828-120">P/Invoke is a technology that allows you to access structs, callbacks and functions in unmanaged libraries from your managed code.</span></span> <span data-ttu-id="f3828-121">P/Invoke API のほとんどは、`System` と `System.Runtime.InteropServices` の 2 つの名前空間に含まれます。</span><span class="sxs-lookup"><span data-stu-id="f3828-121">Most of the P/Invoke API is contained in two namespaces: `System` and `System.Runtime.InteropServices`.</span></span> <span data-ttu-id="f3828-122">これらの 2 つの名前空間を使用して、ネイティブ コンポーネントと通信する方法を記述する属性にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="f3828-122">Using these two namespaces will allow you access to the attributes that describe how you want to communicate with the native component.</span></span>

<span data-ttu-id="f3828-123">最も一般的な例から始めましょう。これはマネージ コードでアンマネージ関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f3828-123">Let’s start from the most common example, and that is calling unmanaged functions in your managed code.</span></span> <span data-ttu-id="f3828-124">コマンドライン アプリケーションからメッセージ ボックスを表示してみましょう。</span><span class="sxs-lookup"><span data-stu-id="f3828-124">Let’s show a message box from a command-line application:</span></span>

```csharp
using System.Runtime.InteropServices;

public class Program {

    // Import user32.dll (containing the function we need) and define
    // the method corresponding to the native function.
    [DllImport("user32.dll")]
    public static extern int MessageBox(IntPtr hWnd, String text, String caption, int options);

    public static void Main(string[] args) {
        // Invoke the function as a regular managed method.
        MessageBox(IntPtr.Zero, "Command-line message box", "Attention!", 0);
    }
}
```

<span data-ttu-id="f3828-125">上の例はとても簡単ですが、マネージ コードからアンマネージ関数を呼び出すために必要なことを示しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-125">The example above is pretty simple, but it does show off what is needed to invoke unmanaged functions from managed code.</span></span> <span data-ttu-id="f3828-126">この例の手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="f3828-126">Let’s step through the example:</span></span>

*   <span data-ttu-id="f3828-127">1 行目は、必要なすべての項目を保持する名前空間 `System.Runtime.InteropServices` のステートメントの使用を示しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-127">Line #1 shows the using statement for the `System.Runtime.InteropServices` which is the namespace that holds all of the items we need.</span></span>
*   <span data-ttu-id="f3828-128">5 行目で `DllImport` 属性を導入しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-128">Line #5 introduces the `DllImport` attribute.</span></span> <span data-ttu-id="f3828-129">この属性は、ランタイムにアンマネージ DLL を読み込むように伝えるため、きわめて重要です。</span><span class="sxs-lookup"><span data-stu-id="f3828-129">This attribute is crucial, as it tells the runtime that it should load the unmanaged DLL.</span></span> <span data-ttu-id="f3828-130">これは、呼び出したい DLL です。</span><span class="sxs-lookup"><span data-stu-id="f3828-130">This is the DLL into which we wish to invoke.</span></span>
*   <span data-ttu-id="f3828-131">6 行目は、P/Invoke 作業の最も重要な箇所です。</span><span class="sxs-lookup"><span data-stu-id="f3828-131">Line #6 is the crux of the P/Invoke work.</span></span> <span data-ttu-id="f3828-132">ここでは、アンマネージと**正確に同じシグネチャ**を持つマネージ メソッドを定義しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-132">It defines a managed method that has the **exact same signature** as the unmanaged one.</span></span> <span data-ttu-id="f3828-133">宣言には新しいキーワード `extern` があることがわかります。これはランタイムに、これが外部メソッドであり、それを呼び出したときに、ランタイムが `DllImport` 属性に指定された DLL からそれを見つける必要があることを伝えます。</span><span class="sxs-lookup"><span data-stu-id="f3828-133">The declaration has a new keyword that you can notice, `extern`, which tells the runtime this is an external method, and that when you invoke it, the runtime should find it in the DLL specified in `DllImport` attribute.</span></span>

<span data-ttu-id="f3828-134">例の残りの部分は、その他のマネージ メソッドと同じように、メソッドを呼び出しているだけです。</span><span class="sxs-lookup"><span data-stu-id="f3828-134">The rest of the example is just invoking the method as you would any other managed method.</span></span>

<span data-ttu-id="f3828-135">サンプルは、macOS の場合も似ています。</span><span class="sxs-lookup"><span data-stu-id="f3828-135">The sample is similar for macOS.</span></span> <span data-ttu-id="f3828-136">変更する必要がある唯一の点が、当然ながら、`DllImport` 属性内のライブラリの名前です。macOS のダイナミック ライブラリの名前付けのスキームが異なるからです。</span><span class="sxs-lookup"><span data-stu-id="f3828-136">One thing that needs to change is, of course, the name of the library in the `DllImport` attribute, as macOS has a different scheme of naming dynamic libraries.</span></span> <span data-ttu-id="f3828-137">下のサンプルでは、`getpid(2)` 関数を使用して、アプリケーションのプロセス ID を取得し、それをコンソールに出力しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-137">The sample below uses the `getpid(2)` function to get the process ID of the application and print it out to the console.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
        [DllImport("libSystem.dylib")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

<span data-ttu-id="f3828-138">これはもちろん Linux でも似ています。</span><span class="sxs-lookup"><span data-stu-id="f3828-138">It is similar on Linux, of course.</span></span> <span data-ttu-id="f3828-139">`getpid(2)` は [POSIX](https://en.wikipedia.org/wiki/POSIX) システム コールであるため、関数名が同じです。</span><span class="sxs-lookup"><span data-stu-id="f3828-139">The function name is same, since `getpid(2)` is [POSIX](https://en.wikipedia.org/wiki/POSIX) system call.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

        // Import the libc and define the method corresponding to the native function.
        [DllImport("libc.so.6")]
        private static extern int getpid();

        public static void Main(string[] args){
            // Invoke the function and get the process ID.
            int pid = getpid();
            Console.WriteLine(pid);
        }
    }
}
```

### <a name="invoking-managed-code-from-unmanaged-code"></a><span data-ttu-id="f3828-140">アンマネージ コードからのマネージ コードの呼び出し</span><span class="sxs-lookup"><span data-stu-id="f3828-140">Invoking managed code from unmanaged code</span></span>

<span data-ttu-id="f3828-141">もちろん、ランタイムは、通信が双方向にフローすることを許可しているため、関数ポインターを使用して、ネイティブ関数からマネージ成果物を呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="f3828-141">Of course, the runtime allows communication to flow both ways which enables you to call into managed artifacts from native functions, using function pointers.</span></span> <span data-ttu-id="f3828-142">マネージ コードで、関数ポインターに最も近いものが、**デリゲート**であるため、これをネイティブ コードからマネージ コードへのコールバックを許可するために使います。</span><span class="sxs-lookup"><span data-stu-id="f3828-142">The closest thing to a function pointer in managed code is a **delegate**, so this is what is used to allow callbacks from native code into managed code.</span></span>

<span data-ttu-id="f3828-143">この機能を使用する方法は、先述のマネージからネイティブへのプロセスに似ています。</span><span class="sxs-lookup"><span data-stu-id="f3828-143">The way to use this feature is similar to managed to native process described above.</span></span> <span data-ttu-id="f3828-144">指定されたコールバックに対し、ユーザーがシグネチャと一致するデリゲートを定義し、それを外部メソッドに渡します。</span><span class="sxs-lookup"><span data-stu-id="f3828-144">For a given callback, you define a delegate that matches the signature, and pass that into the external method.</span></span> <span data-ttu-id="f3828-145">ランタイムは、他のすべてのことを処理します。</span><span class="sxs-lookup"><span data-stu-id="f3828-145">The runtime will take care of everything else.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace ConsoleApplication1 {

    class Program {

        // Define a delegate that corresponds to the unmanaged function.
        delegate bool EnumWC(IntPtr hwnd, IntPtr lParam);

        // Import user32.dll (containing the function we need) and define
        // the method corresponding to the native function.
        [DllImport("user32.dll")]
        static extern int EnumWindows(EnumWC lpEnumFunc, IntPtr lParam);

        // Define the implementation of the delegate; here, we simply output the window handle.
        static bool OutputWindow(IntPtr hwnd, IntPtr lParam) {
            Console.WriteLine(hwnd.ToInt64());
            return true;
        }

        static void Main(string[] args) {
            // Invoke the method; note the delegate as a first parameter.
            EnumWindows(OutputWindow, IntPtr.Zero);
        }
    }
}
```

<span data-ttu-id="f3828-146">例の手順に従う前に、使用する必要があるアンマネージ関数のシグネチャについて見直しておくのはよいことです。</span><span class="sxs-lookup"><span data-stu-id="f3828-146">Before we walk through our example, it is good to go over the signatures of the unmanaged functions we need to work with.</span></span> <span data-ttu-id="f3828-147">すべてのウィンドウを列挙するために呼び出す関数は、次のシグネチャを持ちます。`BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="f3828-147">The function we want to call to enumerate all of the windows has the following signature: `BOOL EnumWindows (WNDENUMPROC lpEnumFunc, LPARAM lParam);`</span></span>

<span data-ttu-id="f3828-148">最初のパラメーターでは、コールバックです。</span><span class="sxs-lookup"><span data-stu-id="f3828-148">The first parameter is a callback.</span></span> <span data-ttu-id="f3828-149">上記のコールバックのシグネチャは次のとおりです。`BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span><span class="sxs-lookup"><span data-stu-id="f3828-149">The said callback has the following signature: `BOOL CALLBACK EnumWindowsProc (HWND hwnd, LPARAM lParam);`</span></span>

<span data-ttu-id="f3828-150">これを踏まえて、例の手順を追っていきましょう。</span><span class="sxs-lookup"><span data-stu-id="f3828-150">With this in mind, let’s walk through the example:</span></span>

*   <span data-ttu-id="f3828-151">例の 8 行目では、アンマネージ コードからのコールバックのシグネチャと一致するデリゲートを定義しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-151">Line #8 in the example defines a delegate that matches the signature of the callback from unmanaged code.</span></span> <span data-ttu-id="f3828-152">マネージ コードで `IntPtr` を使用して、LPARAM および HWND 型を表す方法に注意してください。</span><span class="sxs-lookup"><span data-stu-id="f3828-152">Notice how the LPARAM and HWND types are represented using `IntPtr` in the managed code.</span></span>
*   <span data-ttu-id="f3828-153">10 行目と 11 行目では、user32.dll ライブラリから `EnumWindows` 関数を導入しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-153">Lines #10 and #11 introduce the `EnumWindows` function from the user32.dll library.</span></span>
*   <span data-ttu-id="f3828-154">13 ～ 16 行目は、デリゲートを実装しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-154">Lines #13 - 16 implement the delegate.</span></span> <span data-ttu-id="f3828-155">この簡単な例では、ハンドルだけコンソールに出力します。</span><span class="sxs-lookup"><span data-stu-id="f3828-155">For this simple example, we just want to output the handle to the console.</span></span>
*   <span data-ttu-id="f3828-156">最後に、19 行目で、外部メソッドを呼び出し、デリゲートを渡しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-156">Finally, in line #19 we invoke the external method and pass in the delegate.</span></span>

<span data-ttu-id="f3828-157">Linux と macOS の例を、以下に示します。</span><span class="sxs-lookup"><span data-stu-id="f3828-157">The Linux and macOS examples are shown below.</span></span> <span data-ttu-id="f3828-158">それらの場合、`libc` C ライブラリに見つかる `ftw` 関数を使用します。</span><span class="sxs-lookup"><span data-stu-id="f3828-158">For them, we use the `ftw` function that can be found in `libc`, the C library.</span></span> <span data-ttu-id="f3828-159">この関数は、ディレクトリ階層をスキャンするために使用し、そのパラメーターの 1 つとして、関数へのポインターを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="f3828-159">This function is used to traverse directory hierarchies and it takes a pointer to a function as one of its parameters.</span></span> <span data-ttu-id="f3828-160">上記のメソッドのシグネチャは次のとおりです。`int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`</span><span class="sxs-lookup"><span data-stu-id="f3828-160">The said function has the following signature: `int (*fn) (const char *fpath, const struct stat *sb, int typeflag)`.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
    public static class Program {

            // Define a delegate that has the same signature as the native function.
            delegate int DirClbk(string fName, StatClass stat, int typeFlag);

            // Import the libc and define the method to represent the native function.
            [DllImport("libc.so.6")]
            static extern int ftw(string dirpath, DirClbk cl, int descriptors);

            // Implement the above DirClbk delegate;
            // this one just prints out the filename that is passed to it.
            static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                    Console.WriteLine(fName);
                    return 0;
            }

            public static void Main(string[] args){
                    // Call the native function.
                    // Note the second parameter which represents the delegate (callback).
                    ftw(".", DisplayEntry, 10);
            }
    }

    // The native callback takes a pointer to a struct. The below class
    // represents that struct in managed code. You can find more information
    // about this in the section on marshalling below.
    [StructLayout(LayoutKind.Sequential)]
    public class StatClass {
            public uint DeviceID;
            public uint InodeNumber;
            public uint Mode;
            public uint HardLinks;
            public uint UserID;
            public uint GroupID;
            public uint SpecialDeviceID;
            public ulong Size;
            public ulong BlockSize;
            public uint Blocks;
            public long TimeLastAccess;
            public long TimeLastModification;
            public long TimeLastStatusChange;
    }
}
```

<span data-ttu-id="f3828-161">macOS の例では、同じ関数を使用していますが、唯一の違いは `DllImport` 属性への引数です。macOS は `libc` を別の場所で保持しているためです。</span><span class="sxs-lookup"><span data-stu-id="f3828-161">macOS example uses the same function, and the only difference is the argument to the `DllImport` attribute, as macOS keeps `libc` in a different place.</span></span>

```csharp
using System;
using System.Runtime.InteropServices;

namespace PInvokeSamples {
        public static class Program {

                // Define a delegate that has the same signature as the native function.
                delegate int DirClbk(string fName, StatClass stat, int typeFlag);

                // Import the libc and define the method to represent the native function.
                [DllImport("libSystem.dylib")]
                static extern int ftw(string dirpath, DirClbk cl, int descriptors);

                // Implement the above DirClbk delegate;
                // this one just prints out the filename that is passed to it.
                static int DisplayEntry(string fName, StatClass stat, int typeFlag) {
                        Console.WriteLine(fName);
                        return 0;
                }

                public static void Main(string[] args){
                        // Call the native function.
                        // Note the second parameter which represents the delegate (callback).
                        ftw(".", DisplayEntry, 10);
                }
        }

        // The native callback takes a pointer to a struct. The below class
        // represents that struct in managed code. You can find more information
        // about this in the section on marshalling below.
        [StructLayout(LayoutKind.Sequential)]
        public class StatClass {
                public uint DeviceID;
                public uint InodeNumber;
                public uint Mode;
                public uint HardLinks;
                public uint UserID;
                public uint GroupID;
                public uint SpecialDeviceID;
                public ulong Size;
                public ulong BlockSize;
                public uint Blocks;
                public long TimeLastAccess;
                public long TimeLastModification;
                public long TimeLastStatusChange;
        }
}
```

<span data-ttu-id="f3828-162">上記の例のどちらも、パラメーターに依存し、どちらの場合もパラメーターは、マネージ型として指定されています。</span><span class="sxs-lookup"><span data-stu-id="f3828-162">Both of the above examples depend on parameters, and in both cases, the parameters are given as managed types.</span></span> <span data-ttu-id="f3828-163">ランタイムは、"正しいこと" を実行し、これらを他方の側で同等のものに処理します。</span><span class="sxs-lookup"><span data-stu-id="f3828-163">Runtime does the "right thing" and processes these into its equivalents on the other side.</span></span> <span data-ttu-id="f3828-164">このプロセスでは、高品質なネイティブ相互運用コードを記述することがきわめて重要であるため、ランタイムが型を_マーシャリング_する際に何が起こるかを見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="f3828-164">Since this process is really important to writing quality native interop code, let’s take a look at what happens when the runtime _marshals_ the types.</span></span>

## <a name="type-marshalling"></a><span data-ttu-id="f3828-165">型のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="f3828-165">Type marshalling</span></span>

<span data-ttu-id="f3828-166">**マーシャ リング**はマネージの境界を越えてネイティブに、またはその逆の必要がある場合に、型を変換するプロセスです。</span><span class="sxs-lookup"><span data-stu-id="f3828-166">**Marshalling** is the process of transforming types when they need to cross the managed boundary into native and vice versa.</span></span>

<span data-ttu-id="f3828-167">マーシャリングが必要な理由は、マネージ コードとアンマネージ コード内の型が異なるためです。</span><span class="sxs-lookup"><span data-stu-id="f3828-167">The reason marshalling is needed is because the types in the managed and unmanaged code are different.</span></span> <span data-ttu-id="f3828-168">マネージ コードで、たとえば、`String` があるとします。アンマネージ環境では、文字列は Unicode ("ワイド")、Unicode 以外、Null 終了、ASCII などです。既定で、P/Invoke サブシステムは既定の動作に基づいて "正しいこと" をしようと試みますが、それらについては [MSDN](https://msdn.microsoft.com/library/zah6xy75.aspx) で確認できます。</span><span class="sxs-lookup"><span data-stu-id="f3828-168">In managed code, for instance, you have a `String`, while in the unmanaged world strings can be Unicode ("wide"), non-Unicode, null-terminated, ASCII, etc. By default, the P/Invoke subsystem will try to do the Right Thing based on the default behavior which you can see on [MSDN](https://msdn.microsoft.com/library/zah6xy75.aspx).</span></span> <span data-ttu-id="f3828-169">ただし、特別な制御が必要な場合、`MarshalAs` 属性を採用して、アンマネージ側で期待する型を指定します。</span><span class="sxs-lookup"><span data-stu-id="f3828-169">However, for those situations where you need extra control, you can employ the `MarshalAs` attribute to specify what is the expected type on the unmanaged side.</span></span> <span data-ttu-id="f3828-170">たとえば、文字列を NULL で終わる ANSI 文字列として送信させる場合は、次のように指定できます。</span><span class="sxs-lookup"><span data-stu-id="f3828-170">For instance, if we want the string to be sent as a null-terminated ANSI string, we could do it like this:</span></span>

```csharp
[DllImport("somenativelibrary.dll")]
static extern int MethodA([MarshalAs(UnmanagedType.LPStr)] string parameter);
```

### <a name="marshalling-classes-and-structs"></a><span data-ttu-id="f3828-171">クラスと構造体のマーシャリング</span><span class="sxs-lookup"><span data-stu-id="f3828-171">Marshalling classes and structs</span></span>

<span data-ttu-id="f3828-172">型のマーシャリングの別の側面は、構造体をアンマネージ メソッドに渡す方法です。</span><span class="sxs-lookup"><span data-stu-id="f3828-172">Another aspect of type marshalling is how to pass in a struct to an unmanaged method.</span></span> <span data-ttu-id="f3828-173">たとえば、一部のアンマネージ メソッドでは、パラメーターとして構造体が必要です。</span><span class="sxs-lookup"><span data-stu-id="f3828-173">For instance, some of the unmanaged methods require a struct as a parameter.</span></span> <span data-ttu-id="f3828-174">このような場合、環境のマネージ部分に対応する構造体またはクラスを作成し、それをパラメーターとして使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3828-174">In these cases, we need to create a corresponding struct or a class in managed part of the world to use it as a parameter.</span></span> <span data-ttu-id="f3828-175">ただし、クラスを定義するだけでは不十分で、マーシャラーに、クラス内のフィールドをアンマネージ構造体にマップする方法を指示する必要もあります。</span><span class="sxs-lookup"><span data-stu-id="f3828-175">However, just defining the class is not enough, we also need to instruct the marshaler how to map fields in the class to the unmanaged struct.</span></span> <span data-ttu-id="f3828-176">これは、`StructLayout` 属性が関与する箇所です。</span><span class="sxs-lookup"><span data-stu-id="f3828-176">This is where the `StructLayout` attribute comes into play.</span></span>

```csharp
[DllImport("kernel32.dll")]
static extern void GetSystemTime(SystemTime systemTime);

[StructLayout(LayoutKind.Sequential)]
class SystemTime {
    public ushort Year;
    public ushort Month;
    public ushort DayOfWeek;
    public ushort Day;
    public ushort Hour;
    public ushort Minute;
    public ushort Second;
    public ushort Milsecond;
}

public static void Main(string[] args) {
    SystemTime st = new SystemTime();
    GetSystemTime(st);
    Console.WriteLine(st.Year);
}
```

<span data-ttu-id="f3828-177">上の例は、`GetSystemTime()` 関数を呼び出す簡単な例を示しています。</span><span class="sxs-lookup"><span data-stu-id="f3828-177">The example above shows off a simple example of calling into `GetSystemTime()` function.</span></span> <span data-ttu-id="f3828-178">興味深いビットは 4 行目にあります。</span><span class="sxs-lookup"><span data-stu-id="f3828-178">The interesting bit is on line 4.</span></span> <span data-ttu-id="f3828-179">この属性は、他方 (アンマネージ) の側でクラスのフィールドを構造体に順番にマップする必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="f3828-179">The attribute specifies that the fields of the class should be mapped sequentially to the struct on the other (unmanaged) side.</span></span> <span data-ttu-id="f3828-180">このことは、下に示すアンマネージ構造体に対応する必要があるため、フィールドの名前付けは重要でなく、それらの順番だけが重要であることを意味します。</span><span class="sxs-lookup"><span data-stu-id="f3828-180">This means that the naming of the fields is not important, only their order is important, as it needs to correspond to the unmanaged struct, shown below:</span></span>

```c
typedef struct _SYSTEMTIME {
  WORD wYear;
  WORD wMonth;
  WORD wDayOfWeek;
  WORD wDay;
  WORD wHour;
  WORD wMinute;
  WORD wSecond;
  WORD wMilliseconds;
} SYSTEMTIME, *PSYSTEMTIME*;
```

<span data-ttu-id="f3828-181">前の例で、これの Linux と macOS の例について既に説明しました。</span><span class="sxs-lookup"><span data-stu-id="f3828-181">We already saw the Linux and macOS example for this in the previous example.</span></span> <span data-ttu-id="f3828-182">下にもう一度示します。</span><span class="sxs-lookup"><span data-stu-id="f3828-182">It is shown again below.</span></span>

```csharp
[StructLayout(LayoutKind.Sequential)]
public class StatClass {
        public uint DeviceID;
        public uint InodeNumber;
        public uint Mode;
        public uint HardLinks;
        public uint UserID;
        public uint GroupID;
        public uint SpecialDeviceID;
        public ulong Size;
        public ulong BlockSize;
        public uint Blocks;
        public long TimeLastAccess;
        public long TimeLastModification;
        public long TimeLastStatusChange;
}
```

<span data-ttu-id="f3828-183">`StatClass` クラスは、UNIX システムで `stat` システム コールによって返される構造体を表します。</span><span class="sxs-lookup"><span data-stu-id="f3828-183">The `StatClass` class represents a structure that is returned by the `stat` system call on UNIX systems.</span></span> <span data-ttu-id="f3828-184">これは、指定したファイルに関する情報を表します。</span><span class="sxs-lookup"><span data-stu-id="f3828-184">It represents information about a given file.</span></span> <span data-ttu-id="f3828-185">上のクラスは、マネージ コードでの stat 構造体表現です。</span><span class="sxs-lookup"><span data-stu-id="f3828-185">The class above is the stat struct representation in managed code.</span></span> <span data-ttu-id="f3828-186">ここでも、クラス内のフィールドはネイティブ構造体と同じ順番である必要があり (これらについては、任意の UNIX 実装の man ページを調べて参照できます)、基になる型が同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="f3828-186">Again, the fields in the class have to be in the same order as the native struct (you can find these by perusing man pages on your favorite UNIX implementation) and they have to be of the same underlying type.</span></span>

## <a name="more-resources"></a><span data-ttu-id="f3828-187">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="f3828-187">More resources</span></span>

*   <span data-ttu-id="f3828-188">[PInvoke.net wiki](http://www.pinvoke.net) は、一般的な Win32 API とそれらを呼び出す方法に関する情報を記載した優れた Wiki です。</span><span class="sxs-lookup"><span data-stu-id="f3828-188">[PInvoke.net wiki](http://www.pinvoke.net) an excellent Wiki with information on common Win32 APIs and how to call them.</span></span>
*   [<span data-ttu-id="f3828-189">MSDN の P/Invoke</span><span class="sxs-lookup"><span data-stu-id="f3828-189">P/Invoke on MSDN</span></span>](https://msdn.microsoft.com/library/zbz07712.aspx)
*   [<span data-ttu-id="f3828-190">P/invoke に関する Mono のドキュメント</span><span class="sxs-lookup"><span data-stu-id="f3828-190">Mono documentation on P/Invoke</span></span>](http://www.mono-project.com/docs/advanced/pinvoke/)
