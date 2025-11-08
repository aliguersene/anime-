<style>
  /* البوت المنبثق */
  #botIcon {
    position: fixed;
    bottom: 20px;
    right: 20px;
    width: 64px;
    height: 64px;
    border-radius: 50%;
    background: linear-gradient(135deg, var(--accent), var(--accent-2));
    display: flex;
    justify-content: center;
    align-items: center;
    color: #111;
    font-size: 30px;
    cursor: pointer;
    box-shadow: 0 4px 18px rgba(0,0,0,0.4);
    z-index: 9999;
  }

  #botPopup {
    position: fixed;
    bottom: 100px;
    right: 20px;
    width: 320px;
    max-height: 480px;
    background: #0f0f10;
    border: 1px solid rgba(255,255,255,0.1);
    border-radius: 14px;
    box-shadow: 0 20px 50px rgba(0,0,0,0.8);
    display: none;
    flex-direction: column;
    z-index: 9999;
    overflow: hidden;
  }

  /* الهيدر والرسائل */
  #botHeader {
    background: linear-gradient(90deg, var(--accent), var(--accent-2));
    padding: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    color: #111;
    font-weight: bold;
  }

  #botHeader button {
    background: transparent;
    border: none;
    font-size: 20px;
    cursor: pointer;
  }

  #botMessages2 {
    flex: 1;
    padding: 10px;
    overflow-y: auto;
    display: flex;
    flex-direction: column;
    gap: 8px;
  }

  #botMessages2 .msg.user {
    align-self: flex-end;
    background: rgba(255,255,255,0.1);
    color: var(--text);
    padding: 8px;
    border-radius: 8px;
  }

  #botMessages2 .msg.bot {
    align-self: flex-start;
    background: rgba(255,59,59,0.15);
    color: var(--text);
    padding: 8px;
    border-radius: 8px;
  }

  #botInputRow {
    display: flex;
    gap: 6px;
    padding: 10px;
    border-top: 1px solid rgba(255,255,255,0.05);
  }

  #botInput2 {
    flex: 1;
    padding: 8px;
    border-radius: 8px;
    border: 1px solid rgba(255,255,255,0.1);
    background: transparent;
    color: var(--text);
  }

  #botSend2 {
    padding: 8px 10px;
    background: linear-gradient(90deg, var(--accent), var(--accent-2));
    border: none;
    border-radius: 8px;
    cursor: pointer;
    color: #111;
  }

  /* responsive */
  @media (max-width:980px){
    .content{grid-template-columns:1fr}
    header{flex-direction:column;align-items:flex-start}
    .logo{width:50px;height:50px}
  }
  @media (max-width:600px){
    h1{font-size:16px}
    nav a{font-size:13px;padding:5px 8px}
    .btn{font-size:13px}
    
    /* تعديل البوت على الهواتف */
    #botPopup{
      right:10px;
      bottom:80px;
      width:calc(100% - 20px);
      max-height:60vh; /* ارتفاع مناسب على الهاتف */
    }
    #botIcon{
      bottom:10px;
      right:10px;
      width:56px;
      height:56px;
      font-size:26px;
    }
  }
</style>
