.. _ecc_ram:

=================
ECC内存
=================

我在购买使用 :ref:`nasse_c246` 了解到，这种针对工作站的主板和 :ref:`xeon_e` 支持的ECC内存和我原先购买的 :ref:`hpe_dl360_gen9` ECC内存是不同的。

ECC内存原理
=============

ECC内存使用类似奇偶校验来解决内存位(bit)写入错误，使用 ``10bit`` 存储一个 ``8bit`` 字节( ``byte`` )和复杂的算法来发现 **单个** ``bit`` 何时发生反转以及原始值是多少(简单来说概率上全部位反转几乎不可能)。

这里多出的2个校验位就是为了确定这个存储字节是否正确以及修复如何完成。 **我没有完全理解**

ECC内存分类
==============

简单来说，所谓的ECC内存有两类:

- **寄存器ECC内存** ( ``Registered ECC RAM`` ): 内存上包含了一个寄存器位于内存控制器(主板上)和内存之间，提供缓存。数据从DIMM上的芯片先读取到这个缓存去，再在下一个时钟周期，缓冲区连接到内存控制器以传输数据
- **无缓冲ECC内存** ( ``Unbuffered ECC RAM`` ): 内存上没有寄存器，内存控制器直接从DIMM上芯片读取数据

Registered ECC RAM 和 Unbuffered ECC RAM 本质上并没有更好或更差的对比，而是适应不同内存容量(插槽)的权衡:

- Registered ECC RAM 允许使用更多内存，但是要牺牲一些速度。大多数情况下，需要尽可能多的内存来弥补运行少慢的内存的不足
- Unbuffered ECC RAM 相对速度较快，但是不支持大量内存

.. warning::

   我最初购买 :ref:`nasse_c246` 是想节约资金投入，利旧自己原先在 :ref:`hpe_dl360_gen9` 购买的大量ECC内存。但是我没有注意到(其实回想起来我是发现这个文字差异的，但是没有深究) ``寄存器ECC内存`` 和 ``无缓冲ECC内存`` 的区别。导致还是得继续投入资金购买内存。

   淘宝上将这种工作站使用的 ``无缓冲ECC内存`` 称为 **纯ECC内存** ，将大型服务器使用的 ``寄存器ECC内存`` 称为 **REG ECC内存** ，请不要搞错像我一样乌龙。

参考
======

- `ECC registered vs ECC unbuffered <https://superuser.com/questions/381875/ecc-registered-vs-ecc-unbuffered>`_

