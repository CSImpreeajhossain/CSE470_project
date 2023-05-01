const chai = require('chai');
const chaiHttp = require('chai-http');
const app = require('../app');

chai.use(chaiHttp);
const expect = chai.expect;

describe('Standard Machinery', () => {
  // Test the homepage
  describe('GET /', () => {
    it('return status code 200 and display the homepage', (done) => {
      chai.request(app)
        .get('/')
        .end((err, res) => {
          expect(err).to.be.null;
          expect(res).to.have.status(200);
          expect(res.text).to.contain('Welcome to Standard_ Machinery');
          done();
        });
    });
  });

  // Test the product page
  describe('GET /products', () => {
    it('return status code 200 and display the product page', (done) => {
      chai.request(app)
        .get('/products')
        .end((err, res) => {
          expect(err).to.be.null;
          expect(res).to.have.status(200);
          expect(res.text).to.contain('Products');
          done();
        });
    });
  });

  // Test adding a product to the cart
  describe('POST /cart/add', () => {
    it('add a product to the cart', (done) => {
      chai.request(app)
        .post('/cart/add')
        .send({ productId: 12345, quantity: 1 })
        .end((err, res) => {
          expect(err).to.be.null;
          expect(res).to.have.status(200);
          expect(res.body.message).to.equal('Product added to cart');
          done();
        });
    });
  });

  // Test viewing the cart
  describe('GET /cart', () => {
    it('return status code 200 and display the cart', (done) => {
      chai.request(app)
        .get('/cart')
        .end((err, res) => {
          expect(err).to.be.null;
          expect(res).to.have.status(200);
          expect(res.text).to.contain('Your Cart');
          done();
        });
    });
  });

  // Test updating the cart
  describe('PUT /cart/update', () => {
    it('should update the cart', (done) => {
      chai.request(app)
        .put('/cart/update')
        .send({ productId: 12345, quantity: 2 })
        .end((err, res) => {
          expect(err).to.be.null;
          expect(res).to.have.status(200);
          expect(res.body.message).to.equal('Cart updated');
          done();
        });
    });
  });

  // Test deleting a product from the cart
  describe('DELETE /cart/delete', () => {
    it('should delete a product from the cart', (done) => {
      chai.request(app)
        .delete('/cart/delete')
        .send({ productId: 12345 })
        .end((err, res) => {
          expect(err).to.be.null;
          expect(res).to.have.status(200);
          expect(res.body.message).to.equal('Product deleted from cart');
          done();
        });
    });
  });
});
