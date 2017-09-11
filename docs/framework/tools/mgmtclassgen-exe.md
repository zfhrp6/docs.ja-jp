---
title: "Mgmtclassgen.exe (厳密型クラス ジェネレーター)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- CIM types
- Management Strongly Typed Class Generator
- WMI class
- Mgmtclassgen.exe
- early-bound managed classes
ms.assetid: 02ce6699-49b5-4a0b-b0d5-1003c491232e
caps.latest.revision: 21
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: f83136265c4002f3ea4872b370b856bfacf4db3d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/28/2017

---
# <a name="mgmtclassgenexe-management-strongly-typed-class-generator"></a><span data-ttu-id="14261-102">Mgmtclassgen.exe (厳密型クラス ジェネレーター)</span><span class="sxs-lookup"><span data-stu-id="14261-102">Mgmtclassgen.exe (Management Strongly Typed Class Generator)</span></span>
<span data-ttu-id="14261-103">厳密型クラス ジェネレーター (Mgmtclassgen.exe) ツールを使用すると、指定した WMI (Windows Management Instrumentation) クラスに対して、事前バインディングされたマネージ クラスをすばやく生成できます。</span><span class="sxs-lookup"><span data-stu-id="14261-103">The Management Strongly Typed Class Generator tool enables you to quickly generate an early-bound managed class for a specified Windows Management Instrumentation (WMI) class.</span></span> <span data-ttu-id="14261-104">生成されたクラスを使用すると、WMI クラスのインスタンスにアクセスするために書く必要のあるコードを簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="14261-104">The generated class simplifies the code you must write to access an instance of the WMI class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14261-105">構文</span><span class="sxs-lookup"><span data-stu-id="14261-105">Syntax</span></span>  
  
```  
mgmtclassgen   
WMIClass [options]   
```  
  
|<span data-ttu-id="14261-106">引数</span><span class="sxs-lookup"><span data-stu-id="14261-106">Argument</span></span>|<span data-ttu-id="14261-107">説明</span><span class="sxs-lookup"><span data-stu-id="14261-107">Description</span></span>|  
|--------------|-----------------|  
|<span data-ttu-id="14261-108">*WMIClass*</span><span class="sxs-lookup"><span data-stu-id="14261-108">*WMIClass*</span></span>|<span data-ttu-id="14261-109">事前バインディングしたマネージ クラスを生成する対象の WMI クラスです。</span><span class="sxs-lookup"><span data-stu-id="14261-109">The Windows Management Instrumentation class for which to generate an early-bound managed class.</span></span>|  
  
|<span data-ttu-id="14261-110">オプション</span><span class="sxs-lookup"><span data-stu-id="14261-110">Option</span></span>|<span data-ttu-id="14261-111">説明</span><span class="sxs-lookup"><span data-stu-id="14261-111">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="14261-112">**/l**  *language*</span><span class="sxs-lookup"><span data-stu-id="14261-112">**/l**  *language*</span></span>|<span data-ttu-id="14261-113">事前バインディングされたマネージ クラスの生成に使用する言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="14261-113">Specifies the language in which to generate the early-bound managed class.</span></span> <span data-ttu-id="14261-114">language 引数として **CS** (C#、既定値)、**VB** (Visual Basic)、**MC** (C++)、または **JS** (JScript) を指定できます。</span><span class="sxs-lookup"><span data-stu-id="14261-114">You can specify **CS** (C#; default), **VB** (Visual Basic),  **MC** (C++), or **JS** (JScript) as the language argument.</span></span>|  
|<span data-ttu-id="14261-115">**/m**  *machine*</span><span class="sxs-lookup"><span data-stu-id="14261-115">**/m**  *machine*</span></span>|<span data-ttu-id="14261-116">WMI クラスが常駐する、接続先のコンピューターを指定します。</span><span class="sxs-lookup"><span data-stu-id="14261-116">Specifies the computer to connect to, where the WMI class resides.</span></span> <span data-ttu-id="14261-117">既定値はローカル コンピューターです。</span><span class="sxs-lookup"><span data-stu-id="14261-117">The default is the local computer.</span></span>|  
|<span data-ttu-id="14261-118">**/n**  *path*</span><span class="sxs-lookup"><span data-stu-id="14261-118">**/n**  *path*</span></span>|<span data-ttu-id="14261-119">WMI クラスが含まれている WMI 名前空間へのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="14261-119">Specifies the path to the WMI namespace that contains the WMI class.</span></span> <span data-ttu-id="14261-120">このオプションを指定しない場合、このツールは既定の **Root\cimv2** 名前空間に *WMIClass*のコードを生成します。</span><span class="sxs-lookup"><span data-stu-id="14261-120">If you do not specify this option, the tool generates code for *WMIClass* in the default **Root\cimv2** namespace.</span></span>|  
|<span data-ttu-id="14261-121">**/o**  *classnamespace*</span><span class="sxs-lookup"><span data-stu-id="14261-121">**/o**  *classnamespace*</span></span>|<span data-ttu-id="14261-122">マネージ コード クラスを生成する先の .NET 名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="14261-122">Specifies the .NET namespace in which to generate the managed code class.</span></span> <span data-ttu-id="14261-123">このオプションを指定しない場合、このツールは WMI 名前空間およびスキーマ プリフィックスを使用して名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="14261-123">If you do not specify this option, the tool generates the namespace using the WMI namespace and the schema prefix.</span></span> <span data-ttu-id="14261-124">スキーマ プリフィックスはクラス名の一部で、アンダースコア (_) 文字の前に付きます。</span><span class="sxs-lookup"><span data-stu-id="14261-124">The schema prefix is the part of the class name preceding the underscore character.</span></span> <span data-ttu-id="14261-125">たとえば、**Root\cimv2** 名前空間内の **Win32_OperatingSystem**クラスの場合、このツールは **ROOT.CIMV2.Win32** にクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="14261-125">For example, for the **Win32_OperatingSystem** class in the **Root\cimv2** namespace, the tool would generate the class in **ROOT.CIMV2.Win32**.</span></span>|  
|<span data-ttu-id="14261-126">**/p**  *filepath*</span><span class="sxs-lookup"><span data-stu-id="14261-126">**/p**  *filepath*</span></span>|<span data-ttu-id="14261-127">生成されたコードを保存するファイルへのパスを指定します。</span><span class="sxs-lookup"><span data-stu-id="14261-127">Specifies the path to the file in which to save the generated code.</span></span> <span data-ttu-id="14261-128">このオプションを指定しない場合、このツールは現在のディレクトリにファイルを作成します。</span><span class="sxs-lookup"><span data-stu-id="14261-128">If you do not specify this option, the tool creates the file in the current directory.</span></span> <span data-ttu-id="14261-129">*WMIClass* 引数を使用して生成したクラスと、そのクラスを保存したファイルには名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="14261-129">It names the class and file in which it generates the class using the *WMIClass* argument.</span></span> <span data-ttu-id="14261-130">クラスおよびファイルの名前は、*WMIClass* の名前と同じです。</span><span class="sxs-lookup"><span data-stu-id="14261-130">The name of the class and the file are the same as the name of the *WMIClass.*</span></span> <span data-ttu-id="14261-131">*WMIClass* にアンダースコア (_) 文字が含まれている場合は、アンダースコア (_) 文字の後に続く、クラス名の一部が使用されます。</span><span class="sxs-lookup"><span data-stu-id="14261-131">If *WMIClass* contains an underscore character, the tool uses the part of the class name following the underscore character.</span></span> <span data-ttu-id="14261-132">たとえば、*WMIClass* 名が **Win32_LogicalDisk** という形式の場合、生成されたクラスおよびファイルには "logicaldisk" という名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="14261-132">For example, if the *WMIClass* name is in the format **Win32_LogicalDisk**, the generated class and file is named "logicaldisk".</span></span> <span data-ttu-id="14261-133">ファイルが既に存在している場合は、既存のファイルが上書きされます。</span><span class="sxs-lookup"><span data-stu-id="14261-133">If a file already exists, the tool overwrites the existing file.</span></span>|  
|<span data-ttu-id="14261-134">**/pw**  *password*</span><span class="sxs-lookup"><span data-stu-id="14261-134">**/pw**  *password*</span></span>|<span data-ttu-id="14261-135">**/m** オプションで指定したコンピューターにログオンするときに使用するパスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="14261-135">Specifies the password to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="14261-136">**/u**  *user name*</span><span class="sxs-lookup"><span data-stu-id="14261-136">**/u**  *user name*</span></span>|<span data-ttu-id="14261-137">**/m** オプションで指定したコンピューターにログオンするときに使用するユーザー名を指定します。</span><span class="sxs-lookup"><span data-stu-id="14261-137">Specifies the user name to use when logging on to a computer specified by the **/m** option.</span></span>|  
|<span data-ttu-id="14261-138">**/?**</span><span class="sxs-lookup"><span data-stu-id="14261-138">**/?**</span></span>|<span data-ttu-id="14261-139">このツールのコマンド構文とオプションを表示します。</span><span class="sxs-lookup"><span data-stu-id="14261-139">Displays command syntax and options for the tool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14261-140">コメント</span><span class="sxs-lookup"><span data-stu-id="14261-140">Remarks</span></span>  
 <span data-ttu-id="14261-141">Mgmtclassgen.exe は、<xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=fullName> メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="14261-141">Mgmtclassgen.exe uses the <xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=fullName> method.</span></span> <span data-ttu-id="14261-142">したがって、任意のカスタム コード プロバイダーを使用して、C#、Visual Basic、および JScript 以外のマネージ言語でコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="14261-142">Therefore, you can use any custom code provider to generate code in managed languages other than C#, Visual Basic, and JScript.</span></span>  
  
 <span data-ttu-id="14261-143">生成されたクラスは、それらのクラスを生成する目的となったスキーマにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="14261-143">Note that generated classes are bound to the schema for which they are generated.</span></span> <span data-ttu-id="14261-144">基になるスキーマが変更された場合に、その変更をこのスキーマに反映するには、クラスを生成し直す必要があります。</span><span class="sxs-lookup"><span data-stu-id="14261-144">If the underlying schema changes, you must regenerate the class if you want it to reflect changes to the schema.</span></span>  
  
 <span data-ttu-id="14261-145">WMI CIM (Common Information Model) 型の、生成されたクラスのデータ型への割り当てを次の表に示します。</span><span class="sxs-lookup"><span data-stu-id="14261-145">The following table shows how WMI Common Information Model (CIM) types map to data types in a generated class:</span></span>  
  
|<span data-ttu-id="14261-146">CIM 型</span><span class="sxs-lookup"><span data-stu-id="14261-146">CIM type</span></span>|<span data-ttu-id="14261-147">生成したクラスのデータ型</span><span class="sxs-lookup"><span data-stu-id="14261-147">Data type in the generated class</span></span>|  
|--------------|--------------------------------------|  
|<span data-ttu-id="14261-148">CIM_SINT8</span><span class="sxs-lookup"><span data-stu-id="14261-148">CIM_SINT8</span></span>|<span data-ttu-id="14261-149">**SByte**</span><span class="sxs-lookup"><span data-stu-id="14261-149">**SByte**</span></span>|  
|<span data-ttu-id="14261-150">CIM_UINT8</span><span class="sxs-lookup"><span data-stu-id="14261-150">CIM_UINT8</span></span>|<span data-ttu-id="14261-151">**Byte**</span><span class="sxs-lookup"><span data-stu-id="14261-151">**Byte**</span></span>|  
|<span data-ttu-id="14261-152">CIM_SINT16</span><span class="sxs-lookup"><span data-stu-id="14261-152">CIM_SINT16</span></span>|<span data-ttu-id="14261-153">**Int16**</span><span class="sxs-lookup"><span data-stu-id="14261-153">**Int16**</span></span>|  
|<span data-ttu-id="14261-154">CIM_UINT16</span><span class="sxs-lookup"><span data-stu-id="14261-154">CIM_UINT16</span></span>|<span data-ttu-id="14261-155">**UInt16**</span><span class="sxs-lookup"><span data-stu-id="14261-155">**UInt16**</span></span>|  
|<span data-ttu-id="14261-156">CIM_SINT32</span><span class="sxs-lookup"><span data-stu-id="14261-156">CIM_SINT32</span></span>|<span data-ttu-id="14261-157">**Int32**</span><span class="sxs-lookup"><span data-stu-id="14261-157">**Int32**</span></span>|  
|<span data-ttu-id="14261-158">SIM_UINT32</span><span class="sxs-lookup"><span data-stu-id="14261-158">SIM_UINT32</span></span>|<span data-ttu-id="14261-159">**UInt32**</span><span class="sxs-lookup"><span data-stu-id="14261-159">**UInt32**</span></span>|  
|<span data-ttu-id="14261-160">CIM_SINT64</span><span class="sxs-lookup"><span data-stu-id="14261-160">CIM_SINT64</span></span>|<span data-ttu-id="14261-161">**Int64**</span><span class="sxs-lookup"><span data-stu-id="14261-161">**Int64**</span></span>|  
|<span data-ttu-id="14261-162">CIM_UINT64</span><span class="sxs-lookup"><span data-stu-id="14261-162">CIM_UINT64</span></span>|<span data-ttu-id="14261-163">**UInt64**</span><span class="sxs-lookup"><span data-stu-id="14261-163">**UInt64**</span></span>|  
|<span data-ttu-id="14261-164">CIM_REAL32</span><span class="sxs-lookup"><span data-stu-id="14261-164">CIM_REAL32</span></span>|<span data-ttu-id="14261-165">**Single**</span><span class="sxs-lookup"><span data-stu-id="14261-165">**Single**</span></span>|  
|<span data-ttu-id="14261-166">CIM_REAL64</span><span class="sxs-lookup"><span data-stu-id="14261-166">CIM_REAL64</span></span>|<span data-ttu-id="14261-167">**Double**</span><span class="sxs-lookup"><span data-stu-id="14261-167">**Double**</span></span>|  
|<span data-ttu-id="14261-168">CIM_BOOLEAN</span><span class="sxs-lookup"><span data-stu-id="14261-168">CIM_BOOLEAN</span></span>|<span data-ttu-id="14261-169">**Boolean**</span><span class="sxs-lookup"><span data-stu-id="14261-169">**Boolean**</span></span>|  
|<span data-ttu-id="14261-170">CIM_String</span><span class="sxs-lookup"><span data-stu-id="14261-170">CIM_String</span></span>|<span data-ttu-id="14261-171">**String**</span><span class="sxs-lookup"><span data-stu-id="14261-171">**String**</span></span>|  
|<span data-ttu-id="14261-172">CIM_DATETIME</span><span class="sxs-lookup"><span data-stu-id="14261-172">CIM_DATETIME</span></span>|<span data-ttu-id="14261-173">**DateTime** または **TimeSpan**</span><span class="sxs-lookup"><span data-stu-id="14261-173">**DateTime** or **TimeSpan**</span></span>|  
|<span data-ttu-id="14261-174">CIM_REFERENCE</span><span class="sxs-lookup"><span data-stu-id="14261-174">CIM_REFERENCE</span></span>|<span data-ttu-id="14261-175">**ManagementPath**</span><span class="sxs-lookup"><span data-stu-id="14261-175">**ManagementPath**</span></span>|  
|<span data-ttu-id="14261-176">CIM_CHAR16</span><span class="sxs-lookup"><span data-stu-id="14261-176">CIM_CHAR16</span></span>|<span data-ttu-id="14261-177">**Char**</span><span class="sxs-lookup"><span data-stu-id="14261-177">**Char**</span></span>|  
|<span data-ttu-id="14261-178">CIM_OBJECT</span><span class="sxs-lookup"><span data-stu-id="14261-178">CIM_OBJECT</span></span>|<span data-ttu-id="14261-179">**ManagementBaseObject**</span><span class="sxs-lookup"><span data-stu-id="14261-179">**ManagementBaseObject**</span></span>|  
|<span data-ttu-id="14261-180">CIM_IUNKNOWN</span><span class="sxs-lookup"><span data-stu-id="14261-180">CIM_IUNKNOWN</span></span>|<span data-ttu-id="14261-181">**オブジェクト**</span><span class="sxs-lookup"><span data-stu-id="14261-181">**Object**</span></span>|  
|<span data-ttu-id="14261-182">CIM_ARRAY</span><span class="sxs-lookup"><span data-stu-id="14261-182">CIM_ARRAY</span></span>|<span data-ttu-id="14261-183">上記のオブジェクトの配列</span><span class="sxs-lookup"><span data-stu-id="14261-183">Array of the above mentioned objects</span></span>|  
  
 <span data-ttu-id="14261-184">WMI クラスを生成する場合は、次の動作に注意してください｡</span><span class="sxs-lookup"><span data-stu-id="14261-184">Note the following behaviors when you generate a WMI class:</span></span>  
  
-   <span data-ttu-id="14261-185">標準パブリック プロパティまたはメソッドの名前と既存のプロパティまたはメソッドの名前が同じになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="14261-185">It is possible for a standard public property or method to have the same name as an existing property or method.</span></span> <span data-ttu-id="14261-186">このような事態が発生した場合、このツールは生成したクラスのプロパティまたはメソッドの名前を変更して、名前付けの競合を回避します。</span><span class="sxs-lookup"><span data-stu-id="14261-186">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
-   <span data-ttu-id="14261-187">生成したクラスのプロパティまたはメソッドの名前がプログラミング言語のキーワード名と同じになる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="14261-187">It is possible for the name of a property or method in a generated class to be a keyword in the target programming language.</span></span> <span data-ttu-id="14261-188">このような事態が発生した場合、このツールは生成したクラスのプロパティまたはメソッドの名前を変更して、名前付けの競合を回避します。</span><span class="sxs-lookup"><span data-stu-id="14261-188">If this occurs, the tool changes the name of the property or method in the generated class to avoid naming conflicts.</span></span>  
  
-   <span data-ttu-id="14261-189">WMI では、修飾子は、クラス、インスタンス、プロパティ、またはメソッドを説明する情報を含む修飾子となります。</span><span class="sxs-lookup"><span data-stu-id="14261-189">In WMI, qualifiers are modifiers that contain information to describe a class, instance, property, or method.</span></span> <span data-ttu-id="14261-190">WMI は、**Read**、**Write**、**Key** などの標準の修飾子を使用して、生成したクラスのプロパティについて説明します。</span><span class="sxs-lookup"><span data-stu-id="14261-190">WMI uses standard qualifiers such as **Read**, **Write**, and **Key** to describe a property in a generated class.</span></span> <span data-ttu-id="14261-191">たとえば、**Read** 修飾子で修飾されたプロパティは、生成したクラスではプロパティ **get** アクセサーだけを伴って定義されます。</span><span class="sxs-lookup"><span data-stu-id="14261-191">For example, a property that is modified with a **Read** qualifier is defined only with a property **get** accessor in the generated class.</span></span> <span data-ttu-id="14261-192">**Read** 修飾子でマークされたプロパティは読み取り専用であるため、**set** アクセサーは定義されません。</span><span class="sxs-lookup"><span data-stu-id="14261-192">Because a property marked with the **Read** qualifier is intended to be read-only, a **set** accessor is not defined.</span></span>  
  
-   <span data-ttu-id="14261-193">数値プロパティを **Values** 修飾子および **ValueMaps** 修飾子によって修飾すると、このプロパティには、指定した許容値しか設定できないことを示すことができます。</span><span class="sxs-lookup"><span data-stu-id="14261-193">A numeric property can be modified by the **Values** and **ValueMaps** qualifiers to indicate that the property can be set only to specified permissible values.</span></span> <span data-ttu-id="14261-194">列挙体は、このような **Values** および **ValueMaps** を使用して生成され、このプロパティは列挙体に割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="14261-194">An enumeration is generated with these **Values** and **ValueMaps** and the property is mapped to the enumeration.</span></span>  
  
-   <span data-ttu-id="14261-195">WMI では、インスタンスを 1 つだけを持つことのできるクラスを説明するために、シングルトンという用語を使用します。</span><span class="sxs-lookup"><span data-stu-id="14261-195">The WMI uses the term singleton to describe a class that can have only one instance.</span></span> <span data-ttu-id="14261-196">シングルトン クラスの既定のコンストラクターは、クラスをそのクラスの唯一のインスタンスに初期化します。</span><span class="sxs-lookup"><span data-stu-id="14261-196">Therefore, the default constructor for a singleton class will initialize the class to the only instance of the class.</span></span>  
  
-   <span data-ttu-id="14261-197">WMI クラスは、オブジェクトであるプロパティを持つ場合があります。</span><span class="sxs-lookup"><span data-stu-id="14261-197">A WMI class can have properties that are objects.</span></span> <span data-ttu-id="14261-198">そのような型の WMI クラスに対して、厳密に型指定されたクラスを生成する場合は、埋め込まれたオブジェクト プロパティの型それぞれに対して厳密に型指定されたクラスを生成することを検討してください。</span><span class="sxs-lookup"><span data-stu-id="14261-198">When you generate a strongly-typed class for this type of WMI class, you should consider generating strongly-typed classes for the types of the embedded object properties.</span></span> <span data-ttu-id="14261-199">これにより、厳密に型指定する方法で、埋め込まれたオブジェクトにアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="14261-199">This will allow you to access the embedded objects in a strongly-typed manner.</span></span> <span data-ttu-id="14261-200">生成されたコードが、埋め込まれたオブジェクトの型を検出できない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="14261-200">Note that the generated code might not be able to detect the type of the embedded object.</span></span> <span data-ttu-id="14261-201">このような場合は、生成されたコード内に、その旨をユーザーに通知するコメントが作成されます。</span><span class="sxs-lookup"><span data-stu-id="14261-201">In this case, a comment will be created in the generated code to notify you of this issue.</span></span> <span data-ttu-id="14261-202">これに応じて、生成された他のクラスをプロパティの型として指定するように、生成したコードを変更できます。</span><span class="sxs-lookup"><span data-stu-id="14261-202">You can then modify the generated code to type the property to the other generated class.</span></span>  
  
-   <span data-ttu-id="14261-203">WMI では、CIM_DATETIME データ型のデータ値は、特定の日時または時間間隔を表すことができます。</span><span class="sxs-lookup"><span data-stu-id="14261-203">In WMI, the data value of the CIM_DATETIME data type can represent either a specific date and time or a time interval.</span></span> <span data-ttu-id="14261-204">データ値が日時を表す場合、生成されたクラスのデータ型は **DateTime** です。</span><span class="sxs-lookup"><span data-stu-id="14261-204">If the data value represents a date and time, the data type in the generated class is **DateTime**.</span></span> <span data-ttu-id="14261-205">データ値が時間間隔を表す場合、生成されたクラスのデータ型は **TimeSpan** です。</span><span class="sxs-lookup"><span data-stu-id="14261-205">If the data value represents a time interval, the data type in the generated class is **TimeSpan**.</span></span>  
  
 <span data-ttu-id="14261-206">Visual Studio .NET のサーバー エクスプローラー管理拡張機能を使用して、厳密に型指定されたクラスを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="14261-206">You can alternately generate a strongly-typed class using the Server Explorer Management Extension in Visual Studio .NET.</span></span>  
  
 <span data-ttu-id="14261-207">WMI の詳細については、プラットフォーム SDK の「**Windows Management Instrumentation**」のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="14261-207">For more information about WMI, see the **Windows Management Instrumentation** topic in the Platform SDK documentation.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="14261-208">使用例</span><span class="sxs-lookup"><span data-stu-id="14261-208">Examples</span></span>  
 <span data-ttu-id="14261-209">**Root\cimv2** 名前空間内の **Win32_LogicalDisk** WMI クラスに対してマネージ クラスを C# コードで生成するコマンドを次に示します。</span><span class="sxs-lookup"><span data-stu-id="14261-209">The following command generates a managed class in C# code for the **Win32_LogicalDisk** WMI class in the **Root\cimv2** namespace.</span></span> <span data-ttu-id="14261-210">このツールは、**ROOT.CIMV2.Win32** 名前空間内の c:\disk.cs にあるソース ファイルにマネージ クラスを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="14261-210">The tool writes the managed class to the source file at c:\disk.cs in the **ROOT.CIMV2.Win32** namespace.</span></span>  
  
```  
mgmtclassgen Win32_LogicalDisk /n root\cimv2 /l CS /p c:\disk.cs  
```  
  
 <span data-ttu-id="14261-211">生成したクラスをプログラムによって使用する方法を次のコード例に示します。</span><span class="sxs-lookup"><span data-stu-id="14261-211">The following code example shows how to use a generated class programmatically.</span></span> <span data-ttu-id="14261-212">まず、クラスのインスタンスが列挙され、パスが出力されます。</span><span class="sxs-lookup"><span data-stu-id="14261-212">First, an instance of the class is enumerated and the path is printed.</span></span> <span data-ttu-id="14261-213">次に、初期化の対象となる生成したクラスのインスタンスが、WMI のインスタンスを使用して作成されます。</span><span class="sxs-lookup"><span data-stu-id="14261-213">Next, an instance of the generated class to be initialized is created with an instance of WMI.</span></span> <span data-ttu-id="14261-214">**Root\cimv2** 名前空間において `Process` は **Win32_Process** に対して生成されたクラスであり、`LogicalDisk` は **Win32_LogicalDisk** に対して生成されたクラスです。</span><span class="sxs-lookup"><span data-stu-id="14261-214">`Process` is the class generated for **Win32_Process** and `LogicalDisk` is the class generated for **Win32_LogicalDisk** in the **Root\cimv2** namespace.</span></span>  
  
```vb  
Imports System  
Imports System.Management  
Imports ROOT.CIMV2.Win32  
  
Public Class App     
   Public Shared Sub Main()        
      ' Enumerate instances of the Win32_process.  
      ' Print the Name property of the instance.  
      Dim ps As Process     
      For Each ps In  Process.GetInstances()  
         Console.WriteLine(ps.Name)  
      Next ps  
  
      ' Initialize the instance of LogicalDisk with  
      ' the WMI instance pointing to logical drive d:.  
      Dim dskD As New LogicalDisk(New _  
         ManagementPath("win32_LogicalDisk.DeviceId=""d:"""))  
      Console.WriteLine(dskD.Caption)  
   End Sub  
End Class  
```  
  
```csharp  
using System;  
using System.Management;  
using ROOT.CIMV2.Win32;  
  
public class App  
{  
   public static void Main()  
   {  
      // Enumerate instances of the Win32_process.  
      // Print the Name property of the instance.  
      foreach(Process ps in Process.GetInstances())  
      {  
         Console.WriteLine(ps.Name);  
      }  
  
      // Initialize the instance of LogicalDisk with  
      // the WMI instance pointing to logical drive d:.  
      LogicalDisk dskD = new LogicalDisk(new ManagementPath(  
        "win32_LogicalDisk.DeviceId=\"d:\""));  
      Console.WriteLine(dskD.Caption);  
   }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="14261-215">関連項目</span><span class="sxs-lookup"><span data-stu-id="14261-215">See Also</span></span>  
 <span data-ttu-id="14261-216"><xref:System.Management></span><span class="sxs-lookup"><span data-stu-id="14261-216"><xref:System.Management></span></span>   
 <span data-ttu-id="14261-217"><xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="14261-217"><xref:System.Management.ManagementClass.GetStronglyTypedClassCode%2A?displayProperty=fullName></span></span>   
 <span data-ttu-id="14261-218"><xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="14261-218"><xref:System.CodeDom.Compiler.CodeDomProvider?displayProperty=fullName></span></span>   
 <span data-ttu-id="14261-219">[ツール](../../../docs/framework/tools/index.md) </span><span class="sxs-lookup"><span data-stu-id="14261-219">[Tools](../../../docs/framework/tools/index.md) </span></span>  
 [<span data-ttu-id="14261-220">コマンド プロンプト</span><span class="sxs-lookup"><span data-stu-id="14261-220">Command Prompts</span></span>](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

