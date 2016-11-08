# FileUpload

How to upload a file from the front end to the back end. 

The React file
    import React from 'react'
    import { observer } from 'mobx-react'
    
    const FileUpload = observer(['stores'], React.createClass({
    
      onFileSelected (event) {
        console.log('onFileSelected', event.target.files[0]);
        const { campaignMessageStore } = this.props.stores.appStore
        campaignMessageStore.uploadFile(event.target.files[0])
      },
    
      render() {
        return (
            <div>
              <input
                type="file"
                ref={el => this.fileInput = el }
                onChange={this.onFileSelected}
              />
            </div>
        )
      }
    }))
    
    export default FileUpload
    

The store method

    store.uploadFile = action('test file upload', (file) => {
    api.testFileUpload(file)
      .end(action('test file upload finish', (err, ans) => {
        console.log(ans);
      }))
    })

The call from the client side to the server using super agent

    testFileUpload(file) {
      const metadata = {
        filename: file.name,
        mimeType: file.type
      }
    
      return request.post(`/api/hack/test`)
        .set("thymeVersion", Globals.version)
        .field('metadata', JSON.stringify(metadata))
        .attach('file', file)
        .withCredentials()
    }
    
Catching the data on the server side, node express and multer
    
    router.post('/hack/test',
      multer({ dest: './thyme-uploads/'}).single('file'),
      (req, res) => {

        console.log(req.body)
        console.log(req.file)
    });
    
    