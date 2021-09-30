# Read NFC By Ndef

> **Lien Chen** *2021-09-30*

* When I try to read NFC, I expected to read by NDEF. But `intent.getAction()` give me "NfcAdapter.ACTION_TECH_DISCOVERED".
* Finally I set **try { intentFilter.addDataType("text/plain"); } catch (IntentFilter.MalformedMimeTypeException e) { e.printStackTrace(); }** finally get NDEF action.

```java=
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        this.tvPid = findViewById(R.id.tv_main_pid);
        this.tvMeasureRecord = this.findViewById(R.id.tv_main_measure_record);

        NfcManager nfcManager = (NfcManager) getSystemService(NFC_SERVICE);
        mNfcAdapter = nfcManager.getDefaultAdapter();

        mPendingIntent = PendingIntent.getActivity(this, 0, new Intent(this, getClass()).addFlags(Intent.FLAG_ACTIVITY_SINGLE_TOP), 0);

        IntentFilter intentFilter = new IntentFilter(NfcAdapter.ACTION_NDEF_DISCOVERED);

        try {
            // Important
            intentFilter.addDataType("text/plain");
        } catch (IntentFilter.MalformedMimeTypeException e) {
            e.printStackTrace();
        }

        filters = new IntentFilter[] {intentFilter, };
        techLists = new String[][] {new String[] {NdefFormatable.class.getName()}, new String[] {Ndef.class.getName()}};
    }

    @Override
    protected void onPause() {
        super.onPause();
        mNfcAdapter.disableForegroundDispatch(this);
    }

    @Override
    protected void onResume() {
        super.onResume();
        if(mNfcAdapter != null) {
            mNfcAdapter.enableForegroundDispatch(this, mPendingIntent, filters, techLists);
        }
    }

    @Override
    protected void onNewIntent(Intent intent) {
        super.onNewIntent(intent);
        if (NfcAdapter.ACTION_NDEF_DISCOVERED.equals(intent.getAction())) {
            NdefMessage[] messages = this.getNdefMessages(intent);
            if (messages != null) {
                for (int index = 0; index < messages.length; index++) {
                    Log.d("Ndef", messages[0].toByteArray());
                }
            }
        } else {
            finish();
        }
    }
```

---

* [NFC android](https://developer.android.com/guide/topics/connectivity/nfc/advanced-nfc)
* [Android - 學習操作NFC](https://dotblogs.com.tw/pou/2013/06/05/105285)
