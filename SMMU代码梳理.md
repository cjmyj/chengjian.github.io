# SMMU代码梳理
[TOC]

## 入口函数arm_ssmmu_device_probe
> 总体栈
> arm_ssmmu_device_probe  驱动初始化入口
> arm_smmu_device_dt_probe 从DT中获取SMMU特定信息
> platform_get_resource(pdev, IORESOURCE_MEM, 0); 从设备树获取SMMU的mmio基地址
> smmu->base = arm_smmu_ioremap(dev, ioaddr, ARM_SMMU_REG_SZ); 将SMMU寄存器映射到内存中
> smmu->base = arm_smmu_ioremap(dev, ioaddr, ARM_SMMU_REG_SZ);  解析设备树的SPI中断
> arm_smmu_device_hw_probe   读取SMMU寄存器，确定硬件和软件能力
> arm_smmu_init_structures    初始化内存数据结构，cmdq evtq priq 队列 bitmap等
> 