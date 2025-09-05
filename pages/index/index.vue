<template>
  <div id="app">
    <h1>Web3 DApp Demo</h1>
    <button @click="connectWallet" v-if="!account">连接钱包</button>
    
    <div v-if="account">
      <p><strong>连接账户:</strong> {{ account }}</p>
      <p><strong>ETH 余额:</strong> {{ ethBalance }} ETH</p>
      <button @click="getBalance">刷新余额</button>
    </div>

    <p v-if="error" style="color: red;">{{ error }}</p>
  </div>
</template>

<script>
import { ethers } from "ethers";

export default {
  name: 'Web3DApp', // 添加组件名
  data() {
    return {
      account: null,
      ethBalance: null,
      error: null,
      ethereumProvider: null,
    }
  },
  mounted() {
    this.checkMetaMask();
  },
  beforeUnmount() {
    // 组件销毁前移除事件监听器，避免内存泄漏
    if (this.ethereumProvider && this.ethereumProvider.removeListener) {
      this.ethereumProvider.removeListener('accountsChanged', this.handleAccountsChanged);
    }
  },
  methods: {
    // 将账户变更处理提取为独立方法，便于移除监听器时引用
    handleAccountsChanged(accounts) {
      if (accounts.length === 0) {
        console.log('请连接钱包');
        this.account = null;
      } else if (accounts[0] !== this.account) {
        this.account = accounts[0];
        this.getBalance();
      }
    },
    
    checkMetaMask() {
      // #ifdef H5
      if (typeof window !== 'undefined' && window.ethereum) {
        this.ethereumProvider = window.ethereum;
        console.log("MetaMask 已检测到");
        
        // 使用具名函数引用，便于后续移除
        this.ethereumProvider.on('accountsChanged', this.handleAccountsChanged);
      } else {
        this.error = "请在支持 MetaMask 的桌面浏览器中打开此页面";
      }
      // #endif
      
      // #ifndef H5
      this.error = "当前环境不支持 MetaMask，请使用浏览器访问此页面";
      // #endif
    },
    
    async connectWallet() {
      this.error = null;
      
      // #ifdef H5
      if (this.ethereumProvider) {
        try {
          const accounts = await this.ethereumProvider.request({ method: 'eth_requestAccounts' });
          this.account = accounts[0];
          console.log("Connected account:", this.account);
          
          // 连接成功后获取余额
          this.getBalance();
        } catch (err) {
          this.error = "用户拒绝了连接请求。";
          console.error(err);
        }
      } else {
        this.error = "未检测到 MetaMask。请安装 MetaMask。";
      }
      // #endif
    },

    async getBalance() {
      if (!this.account || !this.ethereumProvider) return;

      try {
        const provider = new ethers.BrowserProvider(this.ethereumProvider);
        // 可以省略获取signer，因为获取余额不需要signer
        // const signer = await provider.getSigner();

        // 获取原生币 (ETH) 余额
        const balance = await provider.getBalance(this.account);
        this.ethBalance = ethers.formatEther(balance);
      } catch (err) {
        this.error = "获取余额失败: " + err.message;
        console.error(err);
      }
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  padding: 10px 20px;
  font-size: 16px;
  cursor: pointer;
  margin: 5px;
}
</style>